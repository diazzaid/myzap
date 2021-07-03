fork from https://github.com/billbarsch/myzap
cara penggunaan

1. git clone https://github.com/diazzaid/myzap.git
2. cd myzap
3. npm install`

### Start server

4. node index.js`

### keep processes alive at every server restart

`npm install -y pm2 -g`

`pm2 start index.js`

`pm2 startup`

## Usage

### Start new whatsapp session / multi session

`http://localhost:3333/start?sessionName=session1`

### Get QRCode
open terminal
![image](https://user-images.githubusercontent.com/25816482/124351487-d37c3c80-dc24-11eb-9ccb-e63b8abb533e.png)



`http://localhost:3333/qrcode?sessionName=session1`
- json (base64)

### Send message (POST method)

```javascript
(async () => {
  const response = await fetch('http://localhost:3333/send-message', {
    method: 'POST',
    headers: {
      'Accept': 'application/json',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(
        {
            seender: "session1", 
            number: '556334140378',
            message:"Hello\nWorld"
        }
    )
  });
  const content = await response.json();

  console.log(content);
})();  
```

### Send File (POST method)

```javascript
(async () => {
    const response = await fetch('http://localhost:3333/send-media', {
    method: 'POST',
    headers: {
      'Accept': 'application/json',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(
        {
            sender: "session1", 
            number: '556334140378',
            base64Data:"44696d61", //hexadecimal
            fileName:"test.txt",
            caption: "Document" //optional
        }
    )
  });
  const content = await response.json();

  console.log(content);
})();  
```

