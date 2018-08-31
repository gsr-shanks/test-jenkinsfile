def tasks = [:]

tasks["task_1"] = {
  stage ("task_1"){    
    node('label_example1') {  
        sh 'echo $NODE_NAME'
    }
  }
}
tasks["task_2"] = {
  stage ("task_2"){    
    node('label_example2') {  
        sh 'echo $NODE_NAME'
    }
  }
}

parallel tasks
