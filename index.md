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
- strings:
  ```
  así
  "así"
  'así'
  incluyendo espacios dentro de las palabras
  ```
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
- puedo anidarlos y combinarlos
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
## Tareas

### Variables
Las variables pueden venir de muchos lados:
- El inventario
- Declaradas explícitamente en un playbook
- Desde la llamada de `ansible_playbook`
- Variables "mágicas" que Ansible calcula por nosotros.

Para usar su valor, usamos jinja con esta sintaxis:

```yaml
- name: Usamos variables por primera vez
  hosts: all
  # Definimos algunas variables para el playbook
  vars:
    ambiente: development
    un_numero: 100
  tasks:
    - name: Muestra las variables que definimos
      ansible.builtin.debug:
        msg: "Mi ambiente es {{ ambiente }} y el numero definido es {{ un_numero }}"

    - name: Muestra la version de S.O.
      ansible.builtin.debug:
        msg: "{{ ansible_distribution }}"

    - name: Puede ser un objeto complejo, como la info del tiempo
      ansible.builtin.debug:
        msg: "{{ ansible_date_time }}"
```

### Registrar valores de tareas y usarlos luego

Ansible escribe lo mínimo necesario a pantalla, recuerda que podemos estar automatizando 20 o 100 equipos. Puedes grabar el resultado de una tarea y luego mostrarlo o tomar decisiones con esta información.

```yaml
- name: Registrar valores y usarlos
  hosts: all
  tasks:
    - name: Averigua el tiempo que lleva corriendo el server
      ansible.builtin.command:
        cmd: uptime
      register: salida_uptime
    - name: Muestra el resultado de toda la tarea
      ansible.builtin.debug:
        msg: "{{ salida_uptime }}"

```
### Loops y filtros

### Condicionales


## Playbooks 4 - Tour de la colección builtin y módulos notables
- copy
- file
- package
- lineinfile
- service
- firewall
- uri


