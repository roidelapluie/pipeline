

echo(message: env.JOB_NAME)
def full_name=env.JOB_NAME.split('/')
def directory_name=full_name[0]
def job_name=full_name[1]
evaluate(new File("default.groovy"))

node {
    git(url: "git://github.com/roidelapluie/${directory_name}")

    //load config
    config_file=new File('.ci.groovy')
    if (config_file.exists()){
        evaluate(new File(".ci.groovy"))
    }

    sh "make"
    sh "make ${test_target}"

    input "Deploy?"

    sh "make deploy"
}




