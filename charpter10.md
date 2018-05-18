# 节点

node 类型
dom1级定义了一个Node接口，改接口将由DOM中的所有节点类型实现，这个Node接口在Javascript中式作为Node类型实现的，除了IE外，在其他所有浏览器中都可以访问到这个类型。

属性值                             |        nodeType   |       中文解释
-----                             |         ------    |       ------
ELEMENT_NODE                      |    1              |       Element类型
ATTRIBUTE_NODE                    |    2              |       Attr类型
TEXT_NODE                         |    3              |       Text类型
CATA_SECTION_NODE                 |    4              |
ENTITY_REFERENCE_NODE             |    5              |
ENTITY_NODE                       |    6              |
PROCESSING_INSTRUCTION_NODE       |    7              |
COMMENT_NODE                      |    8              |       Comment 类型
DOCUMENT_NODE                     |    9              |       Document 类型
DOCUMENT_TYPE_NODE                |    10             |       DocumentFragment 类型
DOCUMENT_FRAGMENT_NODE            |    11             |
NOTATION_NODE                     |    12             |