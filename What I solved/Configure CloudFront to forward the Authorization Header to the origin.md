## How can I configure CloudFront to forward the Authorization header to the origin?

https://aws.amazon.com/premiumsupport/knowledge-center/cloudfront-authorization-header/ <br/>
https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/using-managed-response-headers-policies.html

## Problem

The origin of my Amazon CloudFront distribution requires that requests include the Authorization header. Because of this, my distribution must forward the Authorization header to the origin.\

## Resolution

### Create a cache policy
1. Follow the steps to create a cache policy using the CloudFront console.
2. Under Cache key settings, for Headers, choose Include the following headers. Then, under Add Headers, select Authorization.
3. Complete all other settings of the cache policy based on the requirements of the behavior that you're attaching the policy to. Then, choose Create.
4. After you create the cache policy, follow the steps to attach the policies to the relevant behavior of your CloudFront distribution.

### Edit an existing cache behavior with legacy cache settings
1. Open the CloudFront console, and then choose your distribution.
2. Choose the Behaviors tab, and then select the path for which you want to forward the Authorization header.
3. Choose Edit.
4. Under Headers, choose Include the following headers. Then, under Add Headers, select Authorization.
5. Choose Save changes.