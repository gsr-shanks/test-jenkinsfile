def stages = ["first","second"]

def tasks = [:]

for (item in stages) {
  stage (item) {
    tasks["win"] = {
      node(any) {
        bat 'echo "check"'
      }
    }
    tasks["mac"] = {
      node(any) {
        sh 'echo "check"'
      }
    }
    parallel task
  }
}
