# Setup Authentication for the Weaviate end-points: 

## Two ways to implement the Weavaite Authentication

# Option#1 - APIKey (Typically for Development)
# In Values.yaml file, replace the Authentication section with the below values:

    authentication:
      apikey:
        enabled: true
        allowed_keys:
         - eyJhbGciOiJIUzI1NiIXVCJ9
         - TJVA95OrM7E20RMHrHDcEfxjoYZgeFONFh7HgQ
        users:
         - readonly@example.com
         - admin@example.com
     anonymous_access:
        enabled: false
     oidc:
       enabled: true
       issuer: https://auth.wcs.api.weaviate.io/auth/realms/SeMI
       username_claim: email
       groups_claim: groups
       client_id: wcs
    authorization:
      admin_list:
        enabled: true
        users:
          - someuser@weaviate.io
          - admin@example.com
        readonly_users:
          - readonly@example.com

# Option#2 - Kubernetes Secrets (Typically for Production )
## Work in Progress 

