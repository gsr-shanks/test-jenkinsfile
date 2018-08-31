pipeline {
    agent any

def stages = ["first","second"]

def tasks = [:]

for (item in stages) {
  stage (item) {
    tasks["win"] = {
      node(mywinnode) {
        bat 'echo "check"'
      }
    }
    tasks["mac"] = {
      node(mymacnode) {
        sh 'echo "check"'
      }
    }
    parallel task
  }
}
