# BGP_Open_Policy
Implementations of BGP Open Policy draft (https://datatracker.ietf.org/doc/draft-ietf-idr-bgp-open-policy/)

## BIRD
BIRD Internter Routing Daemon (https://bird.network.cz/; source code: https://gitlab.labs.nic.cz/labs/bird) no longer updating their source code on Github anymore, so I decided to put the code in patch format.

Previous versions of code for previous versions of the draft you can find on https://github.com/QratorLabs/bird.

### Applying
To apply new functionality use `git apply xxx.patch` on a corresponding BIRD version.

### Usage
To use new functionality add the following lines in the config:

```
protocol bgp {
  ...
  local_role provider;
  strict_mode;
}
```
where other possible **local_role** values are: *provider*, *customer*, *peer*, *rs_client* (for IX members) and *rs_server* (for RS themselves).

## FRR
Source code with patch can be find in https://github.com/error2407/frr

### Usage
To use new functionality use the following sintax:

```
neighbor <A.B.C.D|X:X::X:X|WORD> local-role <peer|provider|customer|rs-server|rs-client>
```
or
```
neighbor <A.B.C.D|X:X::X:X|WORD> local-role <peer|provider|customer|rs-server|rs-client> strict-mode
```
