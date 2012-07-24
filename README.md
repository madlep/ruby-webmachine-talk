Most apps do REST/HTTP badly.
Rails does CRUD nicely. BUT. REST > CRUD
Doing it properly requires a lot of manually crafted logic  
Authentication/Authorization
Content-Type/Language/Character-Set negotiation
Caching
Redirects
Language
HTTP verbs
middleware for this, or in app logic? Is both. Where does it live?
in app, lots of copy/paste
in middleware, coupling to app
http RFC logic encoded into FSM
Make web app logic based around HTTP as abstraction, not MVC shaped
Erlang library by Basho (Riak developers)
Ruby port of this
http://webmachine.basho.com/
https://github.com/basho/webmachine
https://github.com/seancribbs/webmachine-ruby
http://wiki.basho.com/images/http-headers-status-v3.png
`respond_to!` equivalent for content type
"Webmachine is a toolkit for easily creating well-behaved HTTP applications."
Sensible defaults for handling HTTP decisions as a starting point
Resources override decisions to build app logic
HTTP web apps - not websockets etc
36 resouce callbacks
dispatching based on URLs -> resources + tokens + init args
basic HELLO WORLD resource
tracing
`resource_exists?` finds + sets model
state of app logic stored as ivars in resource (e.g. found model)
funky - `post_is_create?` `create_path` needs to generate path before parsing request - can't do Rails style create + redirect
if wanting to redirect to pretty URL - probably want a PUT anyway, not a POST
`create_path` feels like a leaky abstraction for common pattern
eschews file ext to indicate media type. Use Content-Type / Accept
simple API, small surface area to learn
helps build an HTTP shaped app. this may or may not be what is required
doesn't help with bad browsers. html forms aren't much here
