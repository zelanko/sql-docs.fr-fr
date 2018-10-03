---
title: Paramètres globaux (boîtes de dialogue) (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e11452b7-ba94-4367-a745-5ccf1764acec
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 23d5177ace1079525ae880b36617904a164ad5d5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47779697"
---
# <a name="global-settings-dialogs--sybasetosql"></a>Paramètres globaux (boîtes de dialogue) (SybaseToSQL)
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
  
