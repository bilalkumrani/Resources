# **Scalability Checklist for Web Apps**

### **Architecture**
- [ ] Confirm backend services are stateless (no local session storage).
- [ ] Set up a load balancer (e.g., AWS ALB, Nginx).
- [ ] Split monolithic components into microservices/serverless functions.
- [ ] Configure auto-scaling rules (min/max instances, CPU/memory thresholds).
- [ ] Test horizontal scaling by spinning up new instances during traffic spikes.

### **Database**
- [ ] Deploy read replicas for high-traffic read operations.
- [ ] Partition/shard databases by user region or data type.
- [ ] Audit slow queries and add missing indexes.
- [ ] Set up database connection pooling (e.g., PgBouncer for PostgreSQL).
- [ ] Enable caching for frequent queries (e.g., Redis).

### **Caching**
- [ ] Integrate CDN (e.g., Cloudflare, AWS CloudFront) for static assets.
- [ ] Cache API responses for idempotent GET requests.
- [ ] Define TTL (time-to-live) policies for cached data.
- [ ] Test cache invalidation workflows.

### **Performance**
- [ ] Move CPU-heavy tasks to async queues (e.g., RabbitMQ, SQS).
- [ ] Compress assets with Brotli/gzip.
- [ ] Enable HTTP/2 or HTTP/3 on the server.
- [ ] Optimize images (WebP format, lazy loading).

### **Security**
- [ ] Add rate limiting to APIs (e.g., 1000 requests/minute per IP).
- [ ] Configure DDoS protection (e.g., AWS Shield, Cloudflare).
- [ ] Enable API request throttling based on user tiers.

### **Monitoring**
- [ ] Track metrics: server CPU/RAM, database latency, cache hit ratio.
- [ ] Set up alerts for 90%+ resource usage.
- [ ] Centralize logs (e.g., AWS CloudWatch, ELK Stack).

### **Cost**
- [ ] Schedule non-production instances to shut down overnight.
- [ ] Replace always-on instances with serverless where possible.
- [ ] Use spot instances for fault-tolerant workloads.

### **Deployment**
- [ ] Automate infrastructure with Terraform/CloudFormation.
- [ ] Test blue-green deployment rollbacks.
- [ ] Ensure CI/CD pipelines run load tests pre-deployment.

### **Testing**
- [ ] Simulate 10x traffic with tools (e.g., JMeter, Locust).
- [ ] Randomly terminate instances to test fault tolerance (chaos engineering).
- [ ] Benchmark database performance under 1000+ concurrent connections.
