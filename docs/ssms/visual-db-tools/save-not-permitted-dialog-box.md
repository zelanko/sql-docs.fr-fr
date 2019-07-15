---
title: Enregistrer (non autorisé), boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.table.tablerecreatenosave.f1
ms.assetid: 7efda8e3-739f-4c97-a497-b8808a0acbea
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 488ec073e47758bc7caff4983f033d44bace67a9
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67679244"
---
# <a name="save-not-permitted-dialog-box"></a>Enregistrer (non autorisé), boîte de dialogue
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
La boîte de dialogue **Enregistrer** (non autorisé) vous prévient que l’enregistrement des modifications n’est pas autorisé car les modifications que vous avez apportées nécessitent la suppression et la recréation des tables répertoriées.  
  
Les actions suivantes peuvent nécessiter la recréation d'une table :  
  
-   Ajout d'une nouvelle colonne au milieu de la table  
  
-   Suppression d'une colonne  
  
-   Modification de la possibilité de valeur nulle d'une colonne  
  
-   Modification de l'ordre des colonnes  
  
-   Modification du type de données d'une colonne  
  
Pour modifier cette option, dans le menu **Outils** , cliquez sur **Options**, développez **Concepteurs**, puis cliquez sur **Concepteurs de bases de données et de tables**. Cochez ou décochez la case **Empêcher l’enregistrement de modifications qui nécessitent une recréation de la table** .  
  
