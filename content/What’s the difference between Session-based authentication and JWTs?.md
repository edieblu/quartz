---
published: true
tags:
  - ✅
sr-due: 2024-12-21
sr-interval: 123
sr-ease: 300
---
⬅️ [[Architecture]]
from Bytebytego newsletter

## Session-Based Authentication
  
In this approach, you store the session information in a database or session store and hand over a session ID to the user.   
  
Think of it like a passenger getting just the Ticket ID of their flight while all other details are stored in the airline’s database.   
  
Here’s how it works: 
1. The user makes a login request and the frontend app sends the request to the backend server. 
2. The backend creates a session using a secret key and stores the data in session storage.
3. The server sends a cookie back to the client with the unique session ID. 
4. The user makes a new request and the browser sends the session ID along with the request. 
5. The server authenticates the user using the session ID. 

## JWT-Based Authentication
  
In the JWT-based approach, you don’t store the session information in the session store.   
The entire information is available within the token.   
  
Think of it like getting the flight ticket along with all the details available on the ticket but encoded.   
  
Here’s how it works: 
1. The user makes a login request and it goes to the backend server. 
2. The server verifies the credentials and issues a JWT. The JWT is signed using a private key and no session storage is involved. 
3. The JWT is passed to the client, either as a cookie or in the response body. Both approaches have their pros and cons but we’ve gone with the cookie approach. 
4. For every subsequent request, the browser sends the cookie with the JWT. 
5. The server verifies the JWT using the secret private key and extracts the user info.

[![graphical user interface, application](https://ci3.googleusercontent.com/meips/ADKq_NZGHxg7tRpEpucRk9ObLBZPAOni0GrdOXfMsMf5GYoVHLXcA4jJC-3bYTuTimK63-9JXcx6oC_LDD4_sQoVElXKsI5Jv07Xa0S_Eoe-XjTLPmBou9vsm1UKGcwXAYaXJ4-Nzb1kZFGeeaOHzM7GZkqhwqCVQRl2lQsjeM8P8ueFjvIjxbYaQ42J-RaM1z6bYQzfX_AvSoW1hi7H33DCOsdtznsAqngFJJYg4b3XFn7_su3gM4T3zjvbKabFtPND1peXPQWjRambSvWPu_MqVyPZpMjPO4M9BBLqOHbGhA=s0-d-e1-ft#https://substackcdn.com/image/fetch/w_550,c_limit,f_auto,q_auto:good,fl_lossy/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F02c27d00-914e-4626-b507-51627646af11_1280x1560.gif "graphical user interface, application")](https://substack.com/redirect/50926e1d-3964-4193-a2c8-7ff0da8edcbd?j=eyJ1IjoiMmtrcG8ifQ.iY0d8N3uUIXkxY9tHeDTpjMDdRUzYKGDut6Fz2UTBVk)