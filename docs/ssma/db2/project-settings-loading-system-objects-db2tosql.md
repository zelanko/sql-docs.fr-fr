---
title: Paramètres (chargement d’objets système) du projet (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9a545233-1b0a-488a-a1ec-c33aa608dcc1
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5c12a2ddb97c6d599e5adfc57277e0a5f64288e5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68060190"
---
# <a name="project-settingsloading-system-objects-db2tosql"></a>Paramètres (chargement d’objets système) du projet (DB2ToSQL)
La page de chargement des objets de système de la **paramètres du projet** boîte de dialogue vous permet de spécifier les objets de système DB2 SSMA convertit et les charge dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Le volet du chargement des objets système n’est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue :  
  
-   Pour spécifier les paramètres pour tous les projets SSMA, sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affichées ou modifiées à partir de **Version cible de migration** déroulante cliquez **général** en bas du volet gauche, puis cliquez sur **le chargement des objets système**.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis cliquez sur **Du chargement des objets système**.  
  
## <a name="default-settings"></a>Paramètres par défaut  
Conversion d’objets système consomme des ressources système et prend du temps. Pour améliorer les performances, SSMA sélectionne uniquement les objets système plus fréquemment utilisées, comme indiqué dans la liste suivante :  
  
-   SYS.DBMS_OUTPUT  
  
-   SYS.DBMS_PIPE  
  
-   SYS.DBMS_UTILITY  
  
-   SYS. STANDARD  
  
-   SYS. UTL_FILE  
  
-   SYS.DBMS_LOB  
  
-   SYS.DBMS_SQL  
  
-   SYS.DBMS_SESSION  
  
Si vos objets DB2 font référence aux objets système supplémentaires, vous devez sélectionner ces objets. Si vous ne sélectionnez pas les objets système qui sont référencés par vos objets de base de données DB2, SSMA signale les erreurs de conversion. Si vous recevez des erreurs de conversion dus à l’absence d’objets système, sélectionnez les objets manquants dans cette boîte de dialogue. Vous pouvez ensuite répéter la conversion en fonction des besoins.  
  
