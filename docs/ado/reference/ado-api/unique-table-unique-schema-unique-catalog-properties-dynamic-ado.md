---
title: Contrôlez les modifications de la Table de Base de l’objet Recordset (ADO) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bcca3701807ebb591a0c083c4f4762b7597b9856
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777387"
---
# <a name="unique-table-unique-schema-unique-catalog-properties-dynamic-ado"></a>Table unique, schéma Unique, Unique catalogue propriétés dynamique (ADO)
Vous permet de contrôle précis des modifications apportées à une table de base de données dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) qui a été formé par une opération de jointure sur plusieurs tables de base.  
  
-   **Table unique** Spécifie le nom de la table de base sur laquelle les mises à jour, insertions et suppressions sont autorisées.  
  
-   **Schéma unique** Spécifie le *schéma*, ou le nom du propriétaire de la table.  
  
-   **Catalogue unique** Spécifie le *catalogue*, ou le nom de la base de données contenant la table.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** valeur qui est le nom d’une table, un schéma ou un catalogue.  
  
## <a name="remarks"></a>Notes  
 La table de base souhaitée est identifiée par son catalogue, schéma, ainsi que les noms de tables. Lorsque le **Unique Table** propriété est définie, les valeurs de la **schéma Unique** ou **catalogue Unique** propriétés permettent de trouver la table de base. Il est prévu, mais pas obligatoire, qu’une ou les deux le **schéma Unique** et **catalogue Unique** propriétés être définies avant le **Unique Table** propriété est définie.  
  
 La clé primaire de la **Unique Table** est traitée comme la clé primaire de l’ensemble du **Recordset**. Il s’agit de la clé qui est utilisée pour n’importe quelle méthode nécessitant une clé primaire.  
  
 Bien que **Unique Table** est défini, le [supprimer](../../../ado/reference/ado-api/delete-method-ado-recordset.md) méthode affecte uniquement la table nommée. Le [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [mise à jour](../../../ado/reference/ado-api/update-method.md), et [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) méthodes affectent aucune table de base sous-jacente appropriée de la **Recordset**.  
  
 **Table unique** doit être spécifié avant de procéder à des resynchronisations personnalisées. Si **Unique Table** n’a pas été spécifié, le [Resync Command](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) propriété n’a aucun effet.  
  
 Une erreur d’exécution des résultats si une table de base unique ne peut pas être trouvée.  
  
 Ces propriétés dynamiques sont toutes ajoutées à la **Recordset** objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection lorsque le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété est définie sur  **adUseClient**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
