### Question - RBAC & SA

Create a service account named "seminar-sa" on the namespace "seminar"

Create a new role named "k8s-seminar" in the namespace "seminar" which only allows "create and update" operations only on resources of type "pods" and "deployments"

Create a new rolebinding name "k8s-seminar-bind" binding to the newly created role to the service account created previously named "seminar-sa".

<details close>
<summary> Solution</summary>
<br>
### Solution

- [RBAC K8s docs](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)

#### 1 - Create a namespace

```sh

kubectl create ns seminar

```

#### 2 - Create service account

```sh

kubectl -n seminar create sa seminar-sa

```

#### 3 - Create role

```sh

kubectl -n seminar create role k8s-seminar --verb=create,update --resource=pods,deployments

```

#### 4 - Create rolebinding

```sh

kubectl -n seminar create rolebinding k8s-seminar-bind --role=k8s-seminar --serviceaccount=seminar:seminar-sa

```
</details>