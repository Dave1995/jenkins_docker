
export CRUMB=`curl -s -u test:11236b662d6edda7c4bb131e7ebdb4784a http://localhost:8080/crumbIssuer/api/json`
11236b662d6edda7c4bb131e7ebdb4784a

curl -s -u test:11236b662d6edda7c4bb131e7ebdb4784a http://localhost:8080/crumbIssuer/api/json
curl -X POST --user test:test http://@localhost:8080/createItem?name=rails_dualboot_poc --data-binary "@files/rails_dualboot_poc.xml" -H "Content-Type:text/xml"
curl -X POST --user test:test http://@localhost:8080/job/rails_dualboot_poc/config.xml --data-binary "@files/rails_dualboot_poc.xml"

-H 'Jenkins-Crumb:0f23a062e0b9b9d13295e26bc8c8e206'


JENKINS_HOST=user:password@localhost:8080
curl -sSL "http://$JENKINS_HOST/pluginManager/api/xml?depth=1&xpath=/*/*/shortName|/*/*/version&wrapper=plugins" | perl -pe 's/.*?<shortName>([\w-]+).*?<version>([^<]+)()(<\/\w+>)+/\1 \2\n/g'|sed 's/ /:/'# jenkins_docker
