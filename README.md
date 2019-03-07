# Install 

```bash
npm -i g artillery-engine-http-ntml
```

You need to either install this package globably, or npm link it globally so that artillery.io can load the module correctly.

Alternatily, you could symlink this module into the artillery.io local node_modules folder and it will also work.

Once installed, your configuration must be setup in order to use the new engine. You must add the engines property to config, and then set config.http.auth to the correct values. type supports either NTML or Negotiate, setting it to Negotiate will give wider compatibility.

You then need to set the engine for any scenario that should use it, as seen below.

Sample yaml configuration

```yaml
config:
  engines:
    http-ntml: {}
  http:
    auth:
      username: user
      password: pass
      type: Negotiate
  target: 'http://ntlm.herokuapp.com/'
  phases:
    - duration: 5
      arrivalRate: 1
scenarios:
  - name: "test"
    engine: http-ntml
    flow:
      - get:
          url: "/"

```