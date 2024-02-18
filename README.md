To setup cloud instance:


1. install git :\
`sudo yum -y install git`
2. install pip :\
`curl -O https://bootstrap.pypa.io/get-pip.py`\
`python3 get-pip.py --user`
3. download repo\
`git clone https://github.com/ilia-iliev/deploydemo.git && cd deploydemo`
4. install requirements\
`python3 -m pip install -r requirements.txt`
5. copy files:\
`scp -i *YOUR PEM FILE* tokenizer.pkl model.pt ec2-user@ec2-YOUR IP ADDRESS.eu-north-1.compute.amazonaws.com:~/deploydemo/`
6. start app\
`uvicorn main:app --port 8000 --host 0.0.0.0`

Don't forget to add rule to allow HTTP requests since this is disabled by default

To request:\
`curl -X POST 'http://*SUBSTITUTE WITH IP ADDRES*:8000/sentiment' -H 'accept: application/json' -H "Content-Type: application/json" -d '"най-глупавият филм, който съм гледал"' `
