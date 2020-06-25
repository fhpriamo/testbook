# Chapter 1

Some JavaScript code:

```javascript
import Queue from 'bee-queue';
import mail from '../tools/mail';
import config from '../config';
import { Job } from '../lib/job';

const queue = new Queue('change-password', { redis: config.get('redis') });

export default new Job(queue, async ({ data }) => {
  const { name, email } = data;

  await mail.send({
    to: `${name} <${email}>`,
    subject: 'Password changed successfully',
    template: 'changePassword',
    context: { name },
  });
});
```
