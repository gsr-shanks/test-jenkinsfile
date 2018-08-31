def tasks = [:]

tasks["task_1"] = {
  stage ("task_1"){    
    node('any') {  
        sh 'echo $NODE_NAME'
    }
  }
}
tasks["task_2"] = {
  stage ("task_2"){    
    node('any') {  
        sh 'echo $NODE_NAME'
    }
  }
}

parallel tasks
