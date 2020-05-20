---
title: Contrôle des modifications apportées à la table de base du recordset (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Unique Table property [ADO]
- Unique Schema property [ADO]
- Unique Catalog property [ADO]
ms.assetid: d0e775d8-e353-46a1-ad10-ed4cc240dfaa
author: rothja
ms.author: jroth
ms.openlocfilehash: ac7fa0cf50a92b2738d3e83d5e7b9d5fac46fd9b
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759515"
---
# <a name="unique-table-unique-schema-unique-catalog-properties-dynamic-ado"></a>Table unique, schéma unique, propriétés de catalogue uniques-dynamique (ADO)
Permet de contrôler étroitement les modifications apportées à une table de base particulière dans un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) formé par une opération de jointure sur plusieurs tables de base.  
  
-   **Table unique** spécifie le nom de la table de base sur laquelle les mises à jour, les insertions et les suppressions sont autorisées.  
  
-   Le **schéma unique** spécifie le *schéma*, ou le nom du propriétaire de la table.  
  
-   **Unique Catalog** spécifie le *catalogue*ou le nom de la base de données contenant la table.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **chaîne** qui est le nom d’une table, d’un schéma ou d’un catalogue.  
  
## <a name="remarks"></a>Notes  
 La table de base souhaitée est identifiée de manière unique par son nom de catalogue, de schéma et de table. Lorsque la propriété de **table unique** est définie, les valeurs des propriétés de **schéma unique** ou **unique de catalogue** sont utilisées pour rechercher la table de base. Il est prévu, mais pas obligatoire, que les propriétés de **schéma unique** et de **catalogue unique** soient définies avant que la propriété de **table unique** soit définie.  
  
 La clé primaire de la **table unique** est traitée comme la clé primaire de l’ensemble du **Recordset**. Il s’agit de la clé utilisée pour toute méthode nécessitant une clé primaire.  
  
 Alors que la **table unique** est définie, la méthode [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md) affecte uniquement la table nommée. Les méthodes [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [Update](../../../ado/reference/ado-api/update-method.md)et [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) affectent les tables de base sous-jacentes appropriées du **Recordset**.  
  
 Une **table unique** doit être spécifiée avant d’exécuter des resynchronisations personnalisées. Si la **table unique** n’a pas été spécifiée, la propriété de [commande Resync](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) n’aura aucun effet.  
  
 Une erreur d’exécution se produit si une table de base unique est introuvable.  
  
 Ces propriétés dynamiques sont toutes ajoutées à la collection de [Propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) de l’objet **Recordset** lorsque la propriété [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) a la valeur **adUseClient**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
