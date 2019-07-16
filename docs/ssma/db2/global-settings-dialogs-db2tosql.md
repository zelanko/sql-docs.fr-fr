---
title: Paramètres globaux (boîtes de dialogue) (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 360e01bb-6347-4e2b-acda-0daa161ed33b
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: de6df03f894d43819cf9d27be3fd35a977631f29
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989632"
---
# <a name="global-settings-dialogs-db2tosql"></a>Paramètres globaux (boîtes de dialogue) (DB2ToSQL)
Utilisez la page de boîtes de dialogue de la **paramètres globaux** boîte de dialogue pour spécifier l’action de l’utilisateur par défaut et les paramètres d’avertissement pour SSMA.  
  
Pour accéder aux paramètres de la boîte de dialogue sur le **outils** menu, sélectionnez **paramètres globaux**, cliquez sur **GUI** en bas du volet gauche, puis sélectionnez **deboîtesdedialogue**.  
  
## <a name="options"></a>Options  
**Avertir avant de remplacer des objets**  
Lorsque SSMA convertit des objets SQL Server, certains objets peuvent déjà exister dans les métadonnées du projet SQL Server. Ces objets peuvent avoir déjà été converties, ou les objets peuvent avoir simplement le même nom dans le schéma cible en tant qu’objets que vous vous apprêtez à convertir.  
  
Utilisez cette option pour spécifier si SSMA doit vous inviter pour remplacer les définitions d’objets en double :  
  
-   Si vous sélectionnez **True**, SSMA affichera une boîte de dialogue d’avertissement lorsqu’il rencontre un objet dupliqué. Dans cette boîte de dialogue, vous pouvez spécifier pour remplacer des objets individuels ou tous les objets en double, ou ignorer des objets individuels ou tous les objets en double.  
  
-   Si vous sélectionnez **False**, le **action par défaut de remplacement de l’objet** option apparaît dans laquelle vous pouvez spécifier l’action par défaut.  
  
**Action par défaut de remplacer l’objet**  
Cette option apparaît si vous sélectionnez **False** pour le **avertir avant de remplacer des objets** option.  
  
Utilisez cette option pour spécifier le comportement de remplacement de l’objet par défaut :  
  
-   Si vous sélectionnez **True**, SSMA remplacera automatiquement des objets dans les métadonnées de projet SQL Server qui ont le même nom et se trouvent dans le même schéma cible en tant que l’objet à convertir.  
  
-   Si vous sélectionnez **False**, SSMA ne remplace pas les métadonnées d’objet lors de la conversion.  
  
