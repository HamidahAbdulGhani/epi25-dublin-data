# Epi25-dublin-data
#Epi25 dublin data download from Terra account to RCSI Local Compute


#on Terminal, start by run interactive session to check the config of gcloud etc. (go for sbatch script if you have all config set-up)

     $  srun -n 2 --mem 4000 --pty bash –i 

#create the new folder on Terminal (on your dir)
#change dir to your folder of interest 

#load the required module, make sure to sign in to rcsi linked google id that linked to your approved workspace Terra email account (both rcsi.ie in my case), using gcloud latest module  

#1. Install/open gcloud SDK in a terminal 

     $ module load gcloud

     $ gsutil version -l 

#Updates are available for some Google Cloud CLI components.  To install them, 

#please run: 
      $ gcloud components update   ##do not run this - you cannot update the software yourself

#gsutil version: 5.27

#checksum: 5cf9fcad0f47bc86542d009bbe69f297 (OK) 

#boto version: 2.49.0 

#python version: 3.11.8 (main, Feb 27 2024, 21:22:27) [Clang 17.0.6 ] 

#OS: Linux 3.10.0-1160.71.1.el7.x86_64 

#multiprocessing available: True 

#using cloud sdk: True 

#pass cloud sdk credentials to gsutil: True 

#config path(s): No config found 

#gsutil path: /home/apps/easybuild/software/gcloud/472.0.0/bin/gsutil 

#compiled crcmod: True 

#installed via package manager: False 

#editable install: False 

#shim enabled: False 

#**Notes: need to remove any extensions, clear the browsing history on the Google, allow third party cookies on Google to avoid blocked Google browser 

#Followed above steps and use command as below in the Terminal 

      $ gcloud auth login 

#Copied that link from Terminal to Google browser (if it is blocked, allow third party cookies etc>as above) 
#Copied and pasted back the authorization code into terminal and it is worked (try to list my buckets) 

#You can verify which Google Account you’ve authorized with gcloud by running the following command. 

      $ gcloud auth list 

      Credentialed Accounts 

      Hamidcccccccsddd0@rcsi.ie

  #pls check available storage space in local compute before download data

#2. Download the data from authorized cloud workspaces
   #gsutils still worked as Aug 2024 (you can work out an equivalent gcloud storage command)
   #you can get the project and workspace name in Terra>Data..copy and paste into here
   
      gsutil -m cp -r "gs://fc-3a833f4b-eb2b<<dummyid>>>37bef7d/Epi25_NINDS_Neale_IRLRCI_Delanty_Cavalleri_McCormack_Epilepsy_GRU-IRB_GSA-MD_Year7" . 
       
      gsutil -m cp -r "gs://fc-dba01022-efbe-46b<<dummyid>>>9641633f/Epi25_NINDS_Neale_IRLRCI_Delanty_Cavalleri_McCormack_Epilepsy_GRU_IRB_WES_Year7/" . 
      
      gsutil -m cp -r gs://fc-dba01022-efbe-46b<<dummyid>>>79641633f/PO-59245_Epi25_NINDS_Neale_IRLRCI_Delanty_Cavalleri_McCormack_Epilepsy_GRU_IRB_WES_Year7_terra_manifest.tsv . 
      
      gsutil -m cp -r gs://fc-dba01022-efbe-b<<dummyid>>>641633f/terra_manifest.tsv . 

#README included were necessary including manifests files 

#after completed the process

       $ module purge 

#Exit from interactive session 


