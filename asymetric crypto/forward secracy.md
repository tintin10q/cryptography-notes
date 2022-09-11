Forward secracy is the property that if the secrets leak that not too much of past communication is leaked.

Just run diffie hellman for every x or every message. These keys are ephemeral key pairs. Leaking the k only leaks the part of it that you secured. But you become much more vunerable against man in the middle.

The solution is that you sign your new ephermal key with a long term key that you only use for signing. If the long term key leaks people can sign on your behaf but not decrypt old stuff. Sounds good. 