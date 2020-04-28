---
title: Utilisation de AddNew dans les modes immédiat et batch | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923624"
---
# <a name="using-addnew-in-immediate-and-batch-modes"></a>Utilisation d’AddNew dans les modes immédiat et batch
Le comportement de la méthode **AddNew** dépend du mode de mise à jour de l’objet **Recordset** et du fait que vous passiez les arguments *FieldList* et *values* .  
  
 En mode de mise à jour immédiate (dans lequel le fournisseur enregistre les modifications apportées à la source de données sous-jacente une fois que vous avez appelé la méthode **Update** ), l’appel de la méthode **AddNew** sans arguments affecte la valeur AdEditAdd à la propriété **EditMode** **.** Le fournisseur met en cache toutes les modifications de valeur de champ localement. L’appel de la méthode **Update** publie le nouvel enregistrement dans la base de données et réinitialise la propriété **EditMode** sur **adEditNone.** Si vous transmettez les arguments *FieldList* et *values* , ADO publie immédiatement le nouvel enregistrement dans la base de données (aucun appel de **mise à jour** n’est nécessaire); la valeur de la propriété **EditMode** ne change pas (**adEditNone**).  
  
 En mode de mise à jour par lot, l’appel de la méthode **AddNew** sans arguments affecte à la propriété **EditMode** la valeur **adEditAdd**. Le fournisseur met en cache toutes les modifications de valeur de champ localement. L’appel de la méthode **Update** ajoute le nouvel enregistrement au **Recordset** actuel et réinitialise la propriété **EditMode** sur **adEditNone**, mais le fournisseur ne publie pas les modifications dans la base de données sous-jacente tant que vous n’appelez pas la méthode **UpdateBatch** . Si vous transmettez les arguments *FieldList* et *values* , ADO envoie le nouvel enregistrement au fournisseur pour le stockage dans un cache ; vous devez appeler la méthode **UpdateBatch** pour poster le nouvel enregistrement dans la base de données sous-jacente. Pour plus d’informations sur **Update** et **UpdateBatch**, consultez mise [à jour et persistance des données](../../../ado/guide/data/updating-and-persisting-data.md).
