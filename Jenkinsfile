

echo(message: env.JOB_NAME)
def full_name=env.JOB_NAME.split('/')
def directory_name=full_name[0]
def job_name=full_name[1]

node {
    git(url: "git://github.com/roidelapluie/${directory_name}")

    //load config
    load '.ci.groovy'

    sh "make"
    sh "make ${test_target}"

    input "Deploy?"

    sh "make deploy"
}




