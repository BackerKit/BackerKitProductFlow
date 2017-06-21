**How do we want to manage error handling?**
* Seems like a reasonable approach is to start with a bang **(!)** on save, create, and update.
* Next step would be check for success and manage errors if not.
* We should think about only using HoneyBadger Notify if we think something outside the norm is going to happen and we want to catch an error and add more behavior. 
* We should try to use Honeybadger only for exceptions. Not for telling us things we kind of already know. “Exceptions are exceptional” --Bosh 
