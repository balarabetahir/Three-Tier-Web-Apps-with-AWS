# Three-Tier-Web-Apps-with-AWS

<img width="990" alt="architecture-complete (6)" src="https://github.com/user-attachments/assets/ffdc83be-da80-42ca-bf34-03057a0135a0" />

The real power of this architecture becomes apparent when your application succeeds. 

The web has come a long way since the early days of static websites. What started as simple pages has evolved into complex applications serving millions of users. If you’re thinking about building a web application today, scalability should be at the core of your design. One effective way to achieve this is by using a three-tier architecture on AWS.

Why Three Tiers?

Breaking an application into three distinct layers — Presentation, Logic, and Data — solves a lot of problems. It makes the system modular. If the user interface changes, the backend can stay the same. If the database grows, the frontend doesn’t have to care. Each layer can scale independently, which is exactly what you want when traffic spikes.

The Presentation Tier

This is what users see. In AWS, this tier is powered by Amazon S3 and CloudFront. S3 hosts your static files — HTML, CSS, JavaScript, images. CloudFront distributes this content globally, making your site load fast anywhere in the world.

Create an S3 bucket.
Enable static website hosting.
Upload your frontend files.
Set permissions for public access.
Configure CloudFront to point to the S3 bucket.
Simple steps, but the result is powerful: a globally accessible, low-latency website.

The Logic Tier

This is where the application thinks. AWS Lambda and API Gateway handle this. Lambda runs your code without servers. API Gateway connects your frontend to Lambda with a REST API.

Write a Lambda function that talks to the database.
Assign it the right IAM role to access DynamoDB.
Create a REST API in API Gateway.
Define GET and POST methods to route traffic to Lambda.
Now your frontend can send requests and get responses — all without managing servers.

The Data Tier

Data is stored in DynamoDB, a NoSQL database that scales automatically. Setting it up is straightforward:

Create a DynamoDB table.
Define a primary key (like userId).
Insert some sample data.
That’s it. Now your application has a durable, scalable data store.

Bringing It All Together

Once the pieces are in place, they need to talk to each other. The frontend must know how to fetch data. That means updating your JavaScript to call the API Gateway endpoint.

Edit script.js to send GET or POST requests to the API.
Deploy the updated files to S3.
Visit your CloudFront URL. If everything is working, your site should load and display data from DynamoDB.

The real power of this architecture becomes apparent when your application succeeds. When traffic spikes, CloudFront handles the increased load on your presentation tier. If you need more computing power, Lambda automatically scales up your logic tier. If you need to store more data, DynamoDB grows with you. You don’t have to rebuild your application to handle success — it’s designed to scale from the beginning.

This approach to building web applications marks a fundamental shift from how we used to build them. Instead of trying to predict how big your application might get and building for that size, you build in a way that can grow or shrink based on actual usage. It’s like having a house that automatically adds rooms when you need them and removes them when you don’t.

Understanding this architecture doesn’t mean you need to use it for everything. Small projects might not need this level of sophistication. But knowing how to build applications this way gives you the tools to handle success when it comes. After all, the goal isn’t just to build something that works — it’s to build something that can keep working no matter how successful it becomes.
