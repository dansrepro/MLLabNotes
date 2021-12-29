# MLLabNotes


gcloud iam service-accounts create my-natlang-sa \

--display-name "my natural language service account"

gcloud iam service-accounts keys create ~/key.json \

--iam-account my-natlang-sa@${GOOGLE_CLOUD_PROJECT}.iam.gserviceaccount.com

export GOOGLE_APPLICATION_CREDENTIALS="/home/$USER/key.json"

gcloud auth activate-service-account my-natlang-sa@qwiklabs-gcp-03-0c12d3531f63.iam.gserviceaccount.com --key-file=$GOOGLE_APPLICATION_CREDENTIALS

gcloud ml language analyze-entities --content="Old Norse texts portray Odin as one-eyed and long-bearded, frequently wielding a spear named Gungnir and wearing a cloak and a broad hat." > result.json

gcloud auth login



gsutil cp result.json gs://qwiklabs-gcp-03-0c12d3531f63-marking/task4-cnl.result

nano request.json

{

"config": {

"encoding":"FLAC",

"languageCode": "en-US"

},

"audio": {

"uri":"gs://cloud-training/gsp323/task4.flac"

}

}

curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json \

"https://speech.googleapis.com/v1/speech:recognize?key=${API_KEY}" > result.json

gsutil cp result.json gs://YOUR_PROJECT-marking/task4-gcs.result

gcloud iam service-accounts create quickstart

gcloud iam service-accounts keys create key.json --iam-account quickstart@${GOOGLE_CLOUD_PROJECT}.iam.gserviceaccount.com

gcloud auth activate-service-account --key-file key.json

export ACCESS_TOKEN=$(gcloud auth print-access-token)

nano request.json

{

"inputUri":"gs://spls/gsp154/video/train.mp4",

"features": [

"TEXT_DETECTION"

]

}

curl -s -H 'Content-Type: application/json' \

-H "Authorization: Bearer $ACCESS_TOKEN" \

'https://videointelligence.googleapis.com/v1/videos:annotate' \

-d @request.json

curl -s -H 'Content-Type: application/json' -H "Authorization: Bearer $ACCESS_TOKEN" 'https://videointelligence.googleapis.com/v1/operations/OPERATION_FROM_PREVIOUS_REQUEST' > result1.json

gsutil cp result1.json gs://YOUR_PROJECT-marking/task4-gvi.result

 [
        {"type":"STRING","name":"guid"},
        {"type":"BOOLEAN","name":"isActive"},
        {"type":"STRING","name":"firstname"},
        {"type":"STRING","name":"surname"},
        {"type":"STRING","name":"company"},
        {"type":"STRING","name":"email"},
        {"type":"STRING","name":"phone"},
        {"type":"STRING","name":"address"},
        {"type":"STRING","name":"about"},
        {"type":"TIMESTAMP","name":"registered"},
        {"type":"FLOAT","name":"latitude"},
        {"type":"FLOAT","name":"longitude"}
    ]
	
	gsutil cp result.json gs://qwiklabs-gcp-03-0c12d3531f63-marking/task4-gcs.result
	
	gcloud iam service-accounts create quickstart

gcloud iam service-accounts keys create key.json --iam-account quickstart@qwiklabs-gcp-03-0c12d3531f63.iam.gserviceaccount.com

gcloud auth activate-service-account --key-file key.json

export ACCESS_TOKEN=$(gcloud auth print-access-token)
