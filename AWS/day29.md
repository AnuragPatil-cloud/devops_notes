## CDN
cdn - Content Delivery Network---> cloudfront 


steps to setup a CDN using AWS CloudFront:
1. Create an S3 bucket and upload your static website files.
2. Go to the CloudFront console and create a new distribution.
3. Select your S3 bucket as the origin.
4. Configure cache settings, SSL, and other options as needed.
5. Deploy the distribution and update your DNS records to point to the CloudFront URL.


## Benefits of using CDN
1. Improved website performance by reducing latency.
2. Scalability to handle high traffic loads.
3. Global reach with edge locations worldwide.




<img width="573" height="530" alt="Screenshot 2026-01-12 at 1 11 24 PM" src="https://github.com/user-attachments/assets/7f0a7158-81f7-4b90-b54a-7b4f89e1dd5e" />


# cache hit and miss (ADVANCED CONCEPTS)
- Cache Hit: When a requested resource is found in the cache, resulting in faster delivery to the user.
- Cache Miss: When a requested resource is not found in the cache, requiring retrieval from the origin server, which may take longer.
- Cache Purging: Removing outdated or unnecessary files from the cache to free up space and ensure users receive the most current content.
