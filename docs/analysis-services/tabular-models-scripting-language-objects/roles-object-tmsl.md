---
title: Roles, objet (TMSL) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 19da91838703adc4ae224a645e1f0a6e65fe032c
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392762"
---
# <a name="roles-object-tmsl"></a>Roles, objet (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Définit un rôle sur le modèle qui spécifie une collection d’autorisations. L’appartenance au rôle est constitué de principes de sécurité de Windows. Vous pouvez définir des filtres sur un rôle pour restreindre l’accès à des objets spécifiques.  
  
## <a name="object-definition"></a>Définition de l'objet  
 Tous les objets ont un ensemble commun de propriétés, notamment le nom, type, description, une collection de propriétés et annotations. **Rôle** objets possèdent également les propriétés suivantes.  
  
 modelPermission  
 Établit une étendue des autorisations sur une base de données. Les valeurs valides sont none,  
                  lecture,  
                  readRefresh,  
                  actualisation  
                  et administrateur. Consultez [rôles et autorisations &#40;Analysis Services&#41; ](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md) pour plus d’informations sur les autorisations de base de données.  
  
 membres  
 Membres se composent d’un nom de membre et l’ID, où nom de membre est l’alias ou le nom convivial d’un principe de sécurité de Windows, et l’ID est l’identificateur de sécurité. Les deux sont spécifiés dans la définition de rôle. Consultez [composants SID](/windows/desktop/SecAuthZ/sid-components) pour plus d’informations sur les identificateurs.  
  
 autorisations de table  
 Une autorisation de table est un objet nommé avec les autorisations définies via une expression DAX. Cette propriété est facultative, utilisé pour appliquer un filtre de sécurité.  
  
## <a name="usage"></a>Utilisation  
 **Rôle** objets sont utilisés dans [Alter, commande &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [Créer commande &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [commande CreateOrReplace &#40;TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), et [commande Delete &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md).  
  
 Un **rôle** objet est une propriété d’un modèle, mais peut également être spécifié en tant que propriété d’un objet de base de données étant donné le mappage entre le modèle et de la base de données.  
  
 Lors de la création, de remplacement ou de modification d’un objet role, spécifiez toutes les propriétés en lecture-écriture de la définition d’objet. L’omission d’une propriété en lecture-écriture est considéré comme une suppression.  
  
## <a name="full-syntax"></a>Syntaxe complète  
 Voici la représentation sous forme de schéma d’un objet de rôle d’un modèle.  
  
```  
"roles": {  
          "type": "array",  
          "items": {  
            "description": "ModelRole object of Tabular Object Model (TOM)",  
            "type": "object",  
            "properties": {  
              "name": {  
                "type": "string"  
              },  
              "description": {  
                "anyOf": [  
                  {  
                    "type": "string"  
                  },  
                  {  
                    "type": "array",  
                    "items": {  
                      "type": "string"  
                    }  
                  }  
                ]  
              },  
              "modelPermission": {  
                "enum": [  
                  "none",  
                  "read",  
                  "readRefresh",  
                  "refresh",  
                  "administrator"  
                ]  
              },  
              "annotations": {  
                "type": "array",  
                "items": {  
                  "description": "Annotation object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "value": {  
                      "anyOf": [  
                        {  
                          "type": "string"  
                        },  
                        {  
                          "type": "array",  
                          "items": {  
                            "type": "string"  
                          }  
                        }  
                      ]  
                    }  
                  },  
                  "additionalProperties": false  
                }  
              },  
              "members": {  
                "type": "array",  
                "items": {  
                  "anyOf": [  
                    {  
                      "description": "WindowsModelRoleMember object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "memberName": {  
                          "type": "string"  
                        },  
                        "memberId": {  
                          "type": "string"  
                        },  
                        "annotations": {  
                          "type": "array",  
                          "items": {  
                            "description": "Annotation object of Tabular Object Model (TOM)",  
                            "type": "object",  
                            "properties": {  
                              "name": {  
                                "type": "string"  
                              },  
                              "value": {  
                                "anyOf": [  
                                  {  
                                    "type": "string"  
                                  },  
                                  {  
                                    "type": "array",  
                                    "items": {  
                                      "type": "string"  
                                    }  
                                  }  
                                ]  
                              }  
                            },  
                            "additionalProperties": false  
                          }  
                        }  
                      },  
                      "additionalProperties": false  
                    },  
                    {  
                      "description": "ExternalModelRoleMember object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "memberName": {  
                          "type": "string"  
                        },  
                        "memberId": {  
                          "type": "string"  
                        },  
                        "identityProvider": {  
                          "type": "string"  
                        },  
                        "memberType": {  
                          "enum": [  
                            "auto",  
                            "user",  
                            "group"  
                          ]  
                        },  
                        "annotations": {  
                          "type": "array",  
                          "items": {  
                            "description": "Annotation object of Tabular Object Model (TOM)",  
                            "type": "object",  
                            "properties": {  
                              "name": {  
                                "type": "string"  
                              },  
                              "value": {  
                                "anyOf": [  
                                  {  
                                    "type": "string"  
                                  },  
                                  {  
                                    "type": "array",  
                                    "items": {  
                                      "type": "string"  
                                    }  
                                  }  
                                ]  
                              }  
                            },  
                            "additionalProperties": false  
                          }  
                        }  
                      },  
                      "additionalProperties": false  
                    }  
                  ]  
                }  
              },  
              "tablePermissions": {  
                "type": "array",  
                "items": {  
                  "description": "TablePermission object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "filterExpression": {  
                      "anyOf": [  
                        {  
                          "type": "string"  
                        },  
                        {  
                          "type": "array",  
                          "items": {  
                            "type": "string"  
                          }  
                        }  
                      ]  
                    },  
                    "annotations": {  
                      "type": "array",  
                      "items": {  
                        "description": "Annotation object of Tabular Object Model (TOM)",  
                        "type": "object",  
                        "properties": {  
                          "name": {  
                            "type": "string"  
                          },  
                          "value": {  
                            "anyOf": [  
                              {  
                                "type": "string"  
                              },  
                              {  
                                "type": "array",  
                                "items": {  
                                  "type": "string"  
                                }  
                              }  
                            ]  
                          }  
                        },  
                        "additionalProperties": false  
                      }  
                    }  
                  },  
                  "additionalProperties": false  
                }  
              }  
            },  
            "additionalProperties": false  
          }  
        }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference [Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;]](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Rôles et autorisations &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  
