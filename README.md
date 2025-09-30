# Epi25-dublin-data
#Epi25 dublin data download from Terra account to RCSI Local Compute


#on Terminal, start by run interactive session to check the config of gcloud etc. (go for sbatch script if you have all config set-up)

     $  srun -n 2 --mem 15000 --pty bash –i 

#create the new folder on Terminal (on your dir)
#change dir to your folder of interest 

#load the required module, make sure to sign in to rcsi account on Google (you rcsi email should linked with google id -please use similar email id for your Terra email account registration (both rcsi.com in my case)

#1. Install/open gcloud SDK in a terminal 

      $ module load gcloud/472.0.0 

#2. Set environment variables 
#For array data: #remove any space 
     
     $ BUCKET='gs://fcxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'  #always put the gs:// before the bucket name
     $ PROJECT_ID='terra-xxxxxx' 

#3. Run commands in cloud environment terminal 

#Step 1. Open a terminal configured to run gcloud on local RCSI machine. 

#Step 2. List files within your gcloud directory with the following command. 

     $ gcloud storage ls $BUCKET 

#ERROR: (gcloud.storage.ls) You do not currently have an active account selected. 

#Please run: 

 # $ gcloud auth login 

#to obtain new credentials. 

#If you have already logged in with a different account, run: 

     $ gcloud config set account x@x.com 

     $ gcloud auth login 

#make sure you sign in first to your google account and Terra via the same .com accounts 
# copy the code from Terminal to your Google Browser #**Notes: need to remove any extensions, clear the browsing history on the Google, allow third party cookies on Google to avoid blocked Google browser 
#Paste the verification code into Terminal
#This above step confirmed that you now login to your Terra credential before moving the data.
#pls check available storage space in local compute before download data

#2. Download the data from authorized Terra cloud workspaces
  
#you can get the project and workspace name in Terra workspace>go to Cloud Info>copy and paste the ID and bucket name as below

#Copy the 10GB genotyping data #less than a min 
     
     $ gcloud storage cp -R $BUCKET . #make sure you in the correct dir otherwise just specify the full path

#After you done with array data download then do the same for WES data
#Do copy the WES Irish data about 43.7GB.make sure you in the correct folder for WES 

#2. Set environment variables 

#For WES data: remove any space, you can the BUCKET and Project ID  this in your approved Terra account (Fexxxxx will do this), Go to Terra Workspace > Cloud Information. Always add the gs:// 

     $ BUCKET='gs://fc-xxxxxxxxxxxxxxxxxxxxxxxxxxxx'    #bucket name 
     $ PROJECT_ID='terra-xxxxxx' 

#you already login to your credential before when you download the array data, no need to repeat it for wes data download 

#Copied 47.3GB WES data #3 mins 
     
     $ gcloud storage cp -R $BUCKET . 

#README included were necessary including manifests files 

#Unload module after completed the process

       $ module purge 

#Exit from an interactive session 
     
       $ exit #exit from session
       $ exit #exit from Terminal

#Congratulations!
       

