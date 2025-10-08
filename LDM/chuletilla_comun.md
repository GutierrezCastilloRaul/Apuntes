# XSD #

## ESTRUCTURA COMÚN DE LOS XSD: ##

Un xsd sigue una estructrua compleja que hay que replicar con cuidado. Eso si, todos tienen que tener en comun esta primera linea:

```xsd
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    ....
</xs:schema>
```

Esto dice que nuestro esquema sigues las regulaciones de la pagina web.

**La siguiente linea sigue indicando el nombre del elemento raíz:**

```xsd
    <xs:element name="pedidos">
        <xs:complexType>
            <xs:sequence>
                ....
            </xs:sequence>
        </xs:complexType>
    </xs:element>
```

### Los elementos pueden ser de distintos tipos: ###

- xs:string
- xs:integer
- xs:boolean
- xs:date
- xs:decimal


### SE SIGUE DESPUES DE CADA ELEMENTO SU TIPO (COMPLEJO O SIMPLE) Y SI ES COMPLEJO LE SIGUE UNA SECUENCIA. ###

Podemos obviamente meter elementos dentro de otros elementos.

Si un elemento no tiene restricciones, podemos poner el tipo junto al nombre:

```xsd
    <xs:element name="pedidos" type="xs:string">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="pedido" type="xs:integer">
                    <xs:complexType>
                        <xs:sequence>
                            ....
                        </xs:sequence>
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
```

Si un elemento es simple pude tener restricciones:

```xsd
*ejemplos con expresiones regulares, numero de telefono, correo y DNI:*

    <xs:element name="telefono">
        <xs:simpleType>
            <xs:restriction base="xs:string">
                <xs:pattern value="\d{3}-\d{3}-\d{3}"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:element> 
    
    <xs:element name="DNI">
        <xs:simpleType>
            <xs:restriction base="xs:string">
                <xs:pattern value="\d{8}[A-Z]"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:element>

    <xs:element name="email">
        <xs:simpleType>
            <xs:restriction base="xs:string">
                <xs:pattern value="[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:element>
```

### TIPOS DE RESTRICCIONES: ##

#### Restriccion de longitud:

```xsd
<xs:element name="NombreLimitado">
 <xs:simpleType>
   <xs:restriction base="xs:string">
     <xs:minLength value="2"/>
     <xs:maxLength value="50"/>
   </xs:restriction>
 </xs:simpleType>
</xs:element>
```
Puede tener Minimo y máximo.

PARA HACER QUE LA PRIMERA LERA SEA MAYUSCULA:

```xsd
<xs:element name="NombreMayuscula">
 <xs:simpleType>
   <xs:restriction base="xs:string">
     <xs:patern value="[A-Z]*">
   </xs:restriction>
 </xs:simpleType>
</xs:element>
```
#### Restriccion por enumeracion: (lista de opciones/estados) :

```xsd
<xs:element name="estado">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:enumeration value="Pendiente"/>
            <xs:enumeration value="Enviado"/>
            <xs:enumeration value="Entregado"/>
            <xs:enumeration value="Cancelado"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
```
#### Restriccion de numero de ocurrencias:

```xsd
<xs:element name="telefono" type="xs:string" minOccurs="0" maxOccurs="3"/>
<!--  xs:maxOccurs="unbounded">
```

### ATRIBUTOS DE UN ELEMENTO: ###
```xsd

<xs:attribute name="codigo" use="required">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <!-- Patrón: A seguido de 3 dígitos -->
            <xs:pattern value="A\d{3}"/>
        </xs:restriction>
    </xs:simpleType>
</xs:attribute>

```

# DTD #

## DTD INTERNA ##

```xml
<!DOCTYPE libro [
<!ELEMENT libro (titulo, autor, editorial)>
<!ELEMENT titulo (#PCDATA)>
<!ELEMENT autor (#PCDATA)>
<!ELEMENT editorial (#PCDATA)>
]>
<libro>
    <titulo>Aprendiendo XML</titulo>
    <autor>Juan Pérez</autor>
    <editorial>Editorial Ejemplo</editorial>
</libro>
```


## DTD EXTERNA ##

### contenido del dtd:

```xml
<!DOCTYPE libro SYSTEM "libro.dtd">
<libro>
    <titulo>Aprendiendo XML</titulo>
    <autor>Juan Pérez</autor>
    <editorial>Editorial Ejemplo</editorial>
</libro>
```

### contenido del xml:

```xml
<!ELEMENT libro (titulo, autor, editorial)>
<!ELEMENT titulo (#PCDATA)>
<!ELEMENT autor (#PCDATA)>
<!ELEMENT editorial (#PCDATA)>
```