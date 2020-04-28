---
title: Modification des enregistrements existants | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], existing records
ms.assetid: 17ce1263-5897-452a-9ea5-c7f96b33df65
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce8679c0c7b20dfaa641918f0447a2f77bfd474a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925437"
---
# <a name="editing-existing-records"></a>Modification d’enregistrements existants
Pour modifier des enregistrements existants, accédez à la ligne que vous souhaitez modifier et modifiez la propriété **valeur** des champs que vous souhaitez modifier. Pour plus d’informations sur la propriété **value** de l’objet **Field** , consultez [examen des données](../../../ado/guide/data/examining-data.md). En fonction de votre type de curseur, vous utiliserez **Update** ou **UpdateBatch** pour renvoyer les modifications à la source de données. Pour plus d’informations, consultez [mise à jour et persistance des données](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Il est généralement plus efficace d’utiliser une procédure stockée avec un objet de commande pour effectuer des mises à jour, ainsi que d’exécuter d’autres opérations, car une procédure stockée ne nécessite pas la création d’un curseur. Pour plus d’informations sur les curseurs, consultez [Présentation des curseurs et des verrous](../../../ado/guide/data/understanding-cursors-and-locks.md).
