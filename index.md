# Taller de Ansible - Teórico

## ¿Qué es Ansible?
Ansible es un motor de automatización de TI de código abierto que automatiza el aprovisionamiento, la gestión de la configuración, la implementación de aplicaciones, la orquestación y muchos otros procesos de TI. Es de uso gratuito y el proyecto se beneficia de la experiencia y la inteligencia de sus miles de contribuyentes.

Red Hat® Ansible Automation Platform combina más de una docena de proyectos upstream en una plataforma empresarial unificada y con seguridad reforzada para la automatización de misión crítica. Se basa en la base del proyecto de código abierto para crear una experiencia de automatización de un extremo a otro para equipos multifuncionales.

https://www.ansible.com/

En Ansible existe un **nodo de control** y uno o más **nodos manejados**

## Instalar Ansible
Necesito instalar en el  **nodo de control**:
  - Linux o
  - WSL (Windows Subsystem for Linux) o
  - MacOS

Instalar usando:
  - Herramientas de la plataforma. Ej: `sudo apt install ansible` o `sudo dnf install ansible-core`
  - pip (PyPI) `pip3 install ansible`

### ¿Qué Incluye?
- `ansible`
- `ansible-playbook`
- `ansible-inventory`
- `ansible-galaxy`
- La colección `ansible.builtin.*` https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html

## YAML YAML Ain't Markup Language - El lenguaje de Ansible

Explicación de los tipos de datos
### Escalares
- números: `1, 10, 3.1416, 2.5E10`
- strings: `así,"así", 'así', varias palabras`
- booleano (verdadero/falso): `true, false`

### Colecciones
- listas de cosas
```yaml
- uno
- dos
- 3
- true
```
- diccionarios/mappings/hash de cosas
```yaml
polar bears: polo norte
penguins: polo sur
neo: 1
trinity: 3
1: one
2: two
```
- Puedo anidarlos y combinarlos
```yaml
albumes_shakira: # tienen un orden
  - Magia
  - Peligro
  - Pies descalzos
patos: # no tienen orden
  Hugo: sobrino
  Paco: sobrino
  Luis: sobrino
```

```yaml
# lista de objetos
- nombre: desayuno
  alimentos:
    - huevos
    - pan
    - jugo
  comi_en_casa: true
- nombre: almuerzo
  alimentos:
    - carne
    - arroz
    - plátano
  comi_en_casa: false
```

### Referencias
YAML Parser online https://yaml-online-parser.appspot.com/
YAML Standard 1.2 https://yaml.org/spec/1.2.2/

## Playbooks - Estructura de un playbook
Los *playbooks* de Ansible son datos especiales en YAML/YML: una lista de *plays*.
Un *play* es un *dictionary/mapping/hash* especial. 

```yaml
- name: El nombre del playbook
  hosts: # una descripción de los nodos manejados
  become: # true o false, para decidir si correr todo como root
  vars: # variables que puedo agregar
  tasks:
    - name: Una tarea
      # ...
    - name: Segunda tarea
      # ...
```

## Módulos - la inteligencia de Ansible

Los módulos están escritos en Python e implementan la complejidad y la inteligencia de Ansible.
- ansible.builtin.debug
- ansible.builtin.command
- ansible.builtin.shell
- ansible.builtin.package

### 

=================
## Tareas 2 - temas avanzados
  - loops
  - delegación
  - condicionales

## Playbooks 4 - Tour de la colección builtin y módulos notables
- copy
- file
- package
- lineinfile
- service
- firewall
- uri


