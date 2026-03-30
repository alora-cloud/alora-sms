

# **API Documentation**

![][image1]

# 

# **Base URL:** [https://api.ipbx.link](https://api.ipbx.link)

**1\. Send Message**

## **Endpoint**

POST /api/send

## **Description**

Queues a message for sending from one sender number to up to 10 recipients.

## **Request Body**

`{`  
 `"api_key": "YOUR_API_KEY",`  
 `"service_type": "sms",`  
 `"sender": "+15550001111",`  
 `"recipient": "+15550002222,+15550003333",`  
 `"message": "Hello from API",`  
 `"tags": "campaign-a"`  
 `}`

## **Fields**

 api\_key (string, required)   
 service\_type (string, required) → e.g., sms  
 sender (string, required) → sender number  
 recipient (string, required) → Comma-separated numbers  
 message (string, required) → Max 2048 characters  
 tags (string, optional) → Optional tag

## **Success Response**

`{`

    `"error": 0,`

    `"msg": "Message queued successfully for sending.",`

    `"data": {`

        `"id": "265",`

        `"time": "2026-03-30T06:50:58Z",`

        `"to": [`

            `"+15550002222",`

	    	   `"+15550003333",`

        `],`

        `"from": "+15550001111",`

        `"message": "wow msg!",`

        `"tags": "campaign-a"`

    `}`

`}`

## **cURL Example**

`curl -X POST "https://api.ipbx.link/api/send"`  
`-H "Content-Type: application/json"`  
`-d '{`  
`"api_key": "YOUR_API_KEY",`  
`"service_type": "sms",`  
`"sender": "+15550001111",`  
`"recipient": "+15550002222,+15550003333",`  
`"message": "Hello from API",`  
`"tags": "campaign-a"`  
`}'`

**2\. Message Report**

## **Endpoint**

GET /api/report/{message\_id}

## **Description**

Returns delivery status of a message.

## **Path Parameter**

message\_id (integer, required) → ID from send API

## **Example Request**

GET /api/report/265?api\_key=YOUR\_API\_KEY

## **Success Response**

`{`  
 `"error": 0,`  
 `"msg": "Message report retrieved successfully",`  
 `"data": {`  
 	`"id": 12345,`  
 	`"time": "2026-03-30T10:15:30Z",`  
 	`"from": 1063,`  
 	`"to": ["+15550002222", "+15550003333"],`  
 	`"message": "wow msg!",`  
 	`"status": "pending"`  
   `}`  
 `}`

## **cURL Example**

curl "[https://api.ipbx.link](https://api.ipbx.link)[/api/report/12345?api\_key=YOUR\_API\_KEY](https://your-domain.com/api/report/12345?api_key=YOUR_API_KEY)"

[image1]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAnAAAAAECAYAAAAOPwJdAAAANElEQVR4Xu3WMQ0AMAwEseAOoJIpqGYvgrzkwcshuLqnHwAAOeoPAADsZuAAAMIYOACAMAOTpGslhjl7rwAAAABJRU5ErkJggg==>