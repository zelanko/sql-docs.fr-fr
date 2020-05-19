---
title: Propriétés dynamiques ADO | Microsoft Docs
ms.prod: sql
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dynamic properties [ADO]
- properties [ADO], dynamic
ms.assetid: d7b06d72-f792-4328-93a2-5006b9e2c581
author: rothja
ms.author: jroth
ms.openlocfilehash: 72fa5fd287b285ca7f917c5969b0e27e11837d25
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82749296"
---
# <a name="ado-dynamic-properties"></a>Propriétés dynamiques ADO
Les propriétés dynamiques peuvent être ajoutées aux collections [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) des objets [Connection](../../../ado/reference/ado-api/connection-object-ado.md), [Command](../../../ado/reference/ado-api/command-object-ado.md)ou [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) . La source de ces propriétés est un fournisseur de données, tel que le [fournisseur de OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)ou un fournisseur de services, tel que le [service de curseur Microsoft pour OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md). Pour plus d’informations sur une propriété dynamique spécifique, reportez-vous à la documentation appropriée du fournisseur de données ou du fournisseur de services.  
  
 L' [index de propriété dynamique ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) fournit une référence croisée entre les noms ado et OLE DB pour chaque propriété dynamique du fournisseur OLE DB standard.  
  
 Les propriétés dynamiques suivantes sont particulièrement intéressantes et sont également documentées dans les sources mentionnées précédemment. Les fonctionnalités spéciales avec ADO sont documentées dans les rubriques d’aide ADO de la liste suivante.  
  
|||  
|-|-|  
|[Optimize](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Spécifie si un index doit être créé sur ce champ.|  
|[Demander](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)|Spécifie si le fournisseur de OLE DB doit inviter l’utilisateur à fournir des informations d’initialisation.|  
|[Reformer le nom](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Spécifie un nom pour l’objet **Recordset** .|  
|[Commande Resync](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Spécifie une chaîne de commande fournie par l’utilisateur que la méthode de **resynchronisation** émet pour actualiser les données de la table nommée dans la propriété dynamique de la **table unique** .|  
|[Table unique, schéma unique, catalogue unique](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|**Table unique** Spécifie le nom de la table de base sur laquelle les mises à jour, les insertions et les suppressions sont autorisées.<br /><br /> **Schéma unique** Spécifie le schéma ou le nom du propriétaire de la table.<br /><br /> **Catalogue unique** Spécifie le catalogue ou le nom de la base de données qui contient la table.|  
|[Mettre à jour la resynchronisation](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)|Spécifie si la méthode **UpdateBatch** est suivie d’une opération de méthode de **resynchronisation** implicite et, le cas échéant, de l’étendue de cette opération.|
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Collections ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Constantes énumérées ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Annexe B : erreurs ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Événements ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Méthodes ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Modèle objet ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Objets et interfaces ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Propriétés ADO](../../../ado/reference/ado-api/ado-properties.md)
