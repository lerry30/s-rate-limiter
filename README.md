## S-RATE-LIMITER ##


S-RATE-LIMITER is a simple rate limiting package designed to help mitigate potential Distributed Denial of Service (DDoS) attacks by preventing overwhelming requests to the backend system. While it cannot guarantee complete protection against DDoS attacks, having an extra layer of defense is preferable to having none at all. This package can effectively block multiple requests at a time, making it suitable for managing multiple requests from a single user, but it may not be able to handle scenarios involving millions of users simultaneously.

### Installation

You can install S-RATE-LIMITER via npm:

```bash
npm install s-rate-limiter
```

### Usage

Here's an example of how you can use S-RATE-LIMITER in your codebase:

```js
import { config, rateLimit } from 's-rate-limiter';

// Configure the rate limiter
config(0.5, { maxRequest: 20, longRestInMiliSec: 1000 * 60 * 1 });

// Check if a user's requests should be denied
const { message, denied } = rateLimit(userId); // Replace 'userId' with the actual user ID or IP address
```

### Configuration

The config function enables you to customize the behavior of the rate limiter. It accepts two parameters:

1. gapPerRequestInMins: This parameter specifies the desired rate limit in requests per minute. It determines the maximum number of requests allowed within a minute.

2. options: An options object that allows for further fine-tuning of the rate limiting mechanism. This object contains the following parameters:

    - maxRequest: A numeric value indicating the maximum number of requests permitted within the specified time frame defined by longRestInMiliSec.

    - longRestInMiliSec: This parameter specifies the duration (in milliseconds) for which the rate limiter will block subsequent requests once the maxRequest limit has been reached. After this timeout period, the rate limiter resets, allowing new requests to be processed.

### Rate Limiting

The rateLimit function is used to check if a particular user, identified by their ID or IP address, has exceeded the specified rate limit. It returns an object containing a message and a boolean value (denied), indicating whether the request should be denied(in a certain duration of time) due to exceeding the rate limit.


### Contributing

Contributions are welcome! Feel free to open issues or submit pull requests on the GitHub repository.

### License

This project is licensed under the MIT License - see the LICENSE file `LICENSE.txt` for details.