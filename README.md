# ws_invocation
---steps for gettinng the webservice authentication go through for the speccific user
cd $MW_HOME/oracle_common/common/bin
./wlst.sh
connect ('weblogic','weblogic1','t3://hostname:7101')

createCred(map="oracle.wsm.security",key="keystore-csf-key",user="owsm",password="welcome1", desc="keystore key")
createCred(map="oracle.wsm.security",key="enc-csf-key",user="orakey",password="welcome1",desc="Encryption key")
createCred(map="oracle.wsm.security",key="<<<APPID-KEY>>",user="specific user",password="Welcome1",desc="Appid key")
for eg.,appid-key FUSION_APPS_SCM_SOA_APPID-KEY

-----
download the default-keystore.jks from the environment
currently it is present in /home/vidsrini/

copied the certificate entries from wsdl and add begin and end certificate entries. refer /home/vidsrini/certificate1.cer & certificate2.cer

cd /scratch/vidsrini/view_storage/vidsrini_vidweb/.jdev_user_home/system11.1.1.9.40.71.30/DefaultDomain/config/fmwconfig/

keytool -importcert -alias pubkey -file certificate1.cer -keystore default-keystore.jks -storepass welcome1
keytool -importcert -alias pubkey1 -file certificate2.cer -keystore default-keystore.jks -storepass welcome1


/scratch/vidsrini/view_storage/vidsrini_vidweb/.jdev_user_home/system11.1.1.9.40.71.30/DefaultDomain/config/fmwconfig/default-keystore.jks

---------
if wsm-pm is not up, go to deployments and click on wsm-pm -> Targets -> select all -> change targets -> check default server -> yes.
-------------
