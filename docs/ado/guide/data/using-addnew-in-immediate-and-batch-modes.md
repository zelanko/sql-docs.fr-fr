---
title: À l’aide de AddNew dans immédiate et Modes de traitement par lots | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: ed314bb9-e188-4658-a68c-a2abc49610be
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 265b1dcd3cdc1aa7f18f0ca54dc2cf54df2da158
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923624"
---
# <a name="using-addnew-in-immediate-and-batch-modes"></a>Utilisation d’AddNew dans les modes immédiat et batch
Le comportement de la **AddNew** méthode varie selon le mode de mise à jour de la **Recordset** objet et si vous passez le *FieldList* et *valeurs*arguments.  
  
 En mode de mise à jour immédiate (dans lequel le fournisseur écrit les modifications à la source de données sous-jacente lorsque vous appelez le **mettre à jour** méthode), l’appel la **AddNew** méthode sans arguments affecte le  **EditMode** propriété **adEditAdd.** Le fournisseur met en cache localement les modifications des valeurs de champ. Appel de la **mise à jour** méthode publie le nouvel enregistrement dans la base de données et réinitialise le **EditMode** propriété **adEditNone.** Si vous passez le *FieldList* et *valeurs* arguments, ADO publie immédiatement le nouvel enregistrement dans la base de données (aucune **mise à jour** appel n’est nécessaire) ; le **EditMode**  valeur de propriété ne change pas (**adEditNone**).  
  
 En mode de mise à jour par lots, appelant le **AddNew** méthode sans arguments affecte le **EditMode** propriété **adEditAdd**. Le fournisseur met en cache localement les modifications des valeurs de champ. Appel de la **mise à jour** méthode ajoute le nouvel enregistrement actuel **Recordset** et réinitialise le **EditMode** propriété **adEditNone**, mais le fournisseur ne valide pas les modifications apportées à la base de données sous-jacente, jusqu'à ce que vous appeliez la **UpdateBatch** (méthode). Si vous passez le *FieldList* et *valeurs* arguments, ADO envoie le nouvel enregistrement dans le fournisseur de stockage dans un cache ; vous devez appeler la **UpdateBatch** méthode pour valider le nouveau Enregistrez la base de données sous-jacente. Pour plus d’informations sur **mise à jour** et **UpdateBatch**, consultez [mise à jour et persistance des données](../../../ado/guide/data/updating-and-persisting-data.md).
