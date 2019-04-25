---
title: Actualiser à partir de la base de données (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 84492f44-c368-4c75-954d-7307a2d2bbc0
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: decc6e25cc8480dfaf041a79baa0972bdd78e569
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62625859"
---
# <a name="refresh-from-database-oracletosql"></a>Actualiser à partir de la base de données (OracleToSQL)
Le **Actualiser à partir de la base de données** boîte de dialogue vous permet de sélectionner les objets à actualiser à partir de la base de données Oracle. Lignes dans la boîte de dialogue sont codées par couleur selon l’état des métadonnées :  
  
-   Si les métadonnées de l’objet a été modifié localement et dans la base de données Oracle, la ligne est bleu.  
  
-   Si les métadonnées de l’objet a changé dans la base de données Oracle, mais pas dans SSMA, la ligne est jaune.  
  
-   Si les métadonnées de l’objet a été modifié localement, mais pas dans la base de données Oracle, la ligne est vert.  
  
-   Si l’objet est nouveau dans la base de données Oracle, la ligne est rose.  
  
Vous pouvez spécifier des paramètres d’actualisation objet par défaut dans le **paramètres du projet** boîte de dialogue. Pour plus d’informations, consultez [paramètres du projet&#40;synchronisation&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
Pour accéder à la **Actualiser à partir de la base de données** boîte de dialogue, avec le bouton droit, un objet dans l’Explorateur de métadonnées d’Oracle et cliquez sur **Actualiser à partir de la base de données**.  
  
## <a name="options"></a>Options  
**Réduction (-)**  
Réduire tous les groupes d’objets pour masquer les objets individuels.  
  
**Expand (+)**  
Développez tous les groupes d’objets pour afficher les objets individuels.  
  
**Masquer/afficher les objets identiques**  
Masquer les objets dans la liste si les métadonnées d’objet sont le même dans la base de données Oracle et de SSMA.  
  
**Actualiser à partir de la base de données (flèche)**  
Utilisez le bouton fléché pour spécifier que les métadonnées pour les objets sélectionnés doivent être mis à jour dans SSMA.  
  
**Faire pas actualiser à partir de la base de données (bouton) X**  
Utilisez le bouton X pour spécifier que les métadonnées pour les objets sélectionnés ne doivent pas mis à jour dans SSMA.  
  
**Légende**  
Affiche un **légende** boîte de dialogue. La légende contient le mappage entre les couleurs de ligne et les États de métadonnées.  
  
Pour conserver le **légende** boîte de dialogue en haut de la **Actualiser à partir de la base de données** boîte de dialogue, sélectionnez le **afficher en haut** case à cocher.  
  
