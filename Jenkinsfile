pipeline {
  agent {
    
  }
  stages {
    stage('osci-tests') {
      steps {
        sh 'env'
        ansiblePlaybook(playbook: 'osci/init.yml', colorized: true, inventoryContent: 'localhost')
      }
    }
    stage('provision') {
      steps {
        sh '''source /root/osci/bin/activate
linchpin -w $WORKSPACE/osci/linchpin --creds-path $WORKSPACE/osci/linchpin/credentials/ up
deactivate

cat $WORKSPACE/osci/linchpin/inventories/openstack_topo.inventory'''
        sh 'ansible -v --ssh-extra-args=\'-o StrictHostKeyChecking=no\' --user=cloud-user --private-key=osci/files/mniranja_linchpin.pem all -i osci/linchpin/inventories/openstack_topo.inventory -m wait_for_connection -a "connect_timeout=10 delay=3 timeout=1500"'
      }
    }
    stage('prepare') {
      steps {
        sh '''source /root/osci/bin/activate
ansible-playbook osci/prepare.yml -i osci/linchpin/inventories/openstack_topo.inventory
deactivate'''
      }
    }
    stage('osci-test') {
      steps {
        ansiblePlaybook(colorized: true, playbook: 'osci/sssd/tests/tests.yml', inventory: 'osci/linchpin/inventories/openstack_topo.inventory', extras: '--user=cloud-user --private-key=osci/files/mniranja_linchpin.pem', sudo: true)
      }
    }
    stage('analyse_&_notify') {
      steps {
        sh '''echo "analysing... ..."
cp osci/sssd/tests/artifacts/junit.xml $WORKSPACE/junit.xml
cp osci/sssd/tests/artifacts/test.log $WORKSPACE/test.log'''
        junit 'junit.xml'
        archiveArtifacts(artifacts: '**/**', fingerprint: true, allowEmptyArchive: true)
      }
    }
    stage('teardown') {
      steps {
        sh '''source /root/osci/bin/activate

linchpin -w $WORKSPACE/osci/linchpin --creds-path $WORKSPACE/osci/linchpin/credentials/ destroy

deactivate'''
        cleanWs(cleanWhenAborted: true, cleanWhenFailure: true, cleanWhenNotBuilt: true, cleanWhenSuccess: true, cleanWhenUnstable: true)
      }
    }
  }
}
