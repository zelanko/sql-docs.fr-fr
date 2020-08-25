---
description: Modification d’enregistrements existants
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9514e727b416935924e3549e2fa10524bab22bd1
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806135"
---
# <a name="editing-existing-records"></a>Modification d’enregistrements existants
Pour modifier des enregistrements existants, accédez à la ligne que vous souhaitez modifier et modifiez la propriété **valeur** des champs que vous souhaitez modifier. Pour plus d’informations sur la propriété **value** de l’objet **Field** , consultez [examen des données](./examining-data.md). En fonction de votre type de curseur, vous utiliserez **Update** ou **UpdateBatch** pour renvoyer les modifications à la source de données. Pour plus d’informations, consultez [mise à jour et persistance des données](./updating-and-persisting-data.md).  
  
 Il est généralement plus efficace d’utiliser une procédure stockée avec un objet de commande pour effectuer des mises à jour, ainsi que d’exécuter d’autres opérations, car une procédure stockée ne nécessite pas la création d’un curseur. Pour plus d’informations sur les curseurs, consultez [Présentation des curseurs et des verrous](./understanding-cursors-and-locks.md).