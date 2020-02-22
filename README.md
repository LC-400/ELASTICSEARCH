Installing elasticsearch V7.6.0 with Lucene V8.4.0 on Debian Jessie running
in Vagrant V1.9.1 on top of Virtualbox V5.1.

One cluster is created on the virtual host.

Installation
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-
key add -

sudo apt-get install apt-transport-https

echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo
tee -a /etc/apt/sources.list.d/elastic-7.x.list

sudo apt-get update && sudo apt-get install elasticsearch

Configuration
By default the elasticsearch service is disabled. Enable with:
sudo systemctl enable elasticsearch.service. Check status with:
sudo systemctl status elasticsearch.service. Start the service with:
sudo systemctl start elasticsearch.service

Confirm that the elasticsearch service is running on localhost on port 9200
with: curl -X GET "localhost:9200". You should see in your terminal a json-
formatted page with the tagline "You Know, for Search". You can also point
your favourite browser this address.

Note: The OpenJDK-Server fails if the VM is running with too low memory
allocated. To verify, run "java -v" to see if this is the case. Journalctl
-u elasticsearch is quiet regarding this memory issue. Adjust the memory 
setting in the Vagrantfile (uncomment VM.memory and adjust as necessary).

