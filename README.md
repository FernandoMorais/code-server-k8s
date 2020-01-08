# code-server-k8s [![MIT license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/FernandoMorais/code-server-k8s/blob/master/LICENSE)

`code-server` is [VS Code](https://github.com/Microsoft/vscode) running on a
remote server, accessible through the browser. For more information about it go to [code-server @ Github](https://github.com/cdr/code-server).

## Getting Started

### Requirements

- A Kubernets cluster running
- Nginx ingress configured an ready to accept ingress objects
- Let's Encrypt controller or wildcard certificate to provide https access
- Ansible 2.8.5 or above
- Python modules: 
    - jmespath (0.9.4)
    - kubernetes (9.0.0)
    - openshift (0.9.0)
    - docker (4.1.0)

### Running

1. Create namespace and configure:  

    ```bash
    ansible-playbook playbook/setup-namespace.yml --extra-vars "code_server_password=P4s$w0rd"
    ```
    *Remenber to change the `code_server_password` properly!*

2. Create the app:  

    ```bash
    ansible-playbook playbook/setup-app.yml
    ```

3. Create and configure the ingress

    ```bash
    ansible-playbook playbook/setup-ingress.yml --extra-vars "k8s_ingress_host=localhost"
    ```
    *Remenber to change the `k8s_ingress_host` properly!*

## License

[MIT](LICENSE)
