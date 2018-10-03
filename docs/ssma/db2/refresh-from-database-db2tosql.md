---
title: Actualiser à partir de la base de données (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 613a8368-b372-443f-8252-fb6dc31a003d
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ef7778854248f194c01254b9cd6f833f67e9cefc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685117"
---
# <a name="refresh-from-database-db2tosql"></a>Actualiser à partir de la base de données (DB2ToSQL)
Le **Actualiser à partir de la base de données** boîte de dialogue vous permet de sélectionner les objets à actualiser à partir de la base de données DB2. Lignes dans la boîte de dialogue sont codées par couleur selon l’état des métadonnées :  
  
-   Si les métadonnées de l’objet a été modifié localement et dans la base de données DB2, la ligne est bleu.  
  
-   Si les métadonnées de l’objet a changé dans la base de données DB2, mais pas dans SSMA, la ligne est jaune.  
  
-   Si les métadonnées de l’objet a été modifié localement, mais pas dans la base de données DB2, la ligne est vert.  
  
-   Si l’objet est nouveau dans la base de données DB2, la ligne est rose.  
  
Vous pouvez spécifier des paramètres d’actualisation objet par défaut dans le **paramètres du projet** boîte de dialogue. Pour plus d’informations, consultez [paramètres du projet&#40;synchronisation&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md).  
  
Pour accéder à la **Actualiser à partir de la base de données** boîte de dialogue, avec le bouton droit, un objet dans l’Explorateur de métadonnées de DB2 et cliquez sur **Actualiser à partir de la base de données**.  
  
## <a name="options"></a>Options  
**Réduction (-)**  
Réduire tous les groupes d’objets pour masquer les objets individuels.  
  
**Développement (+)**  
Développez tous les groupes d’objets pour afficher les objets individuels.  
  
**Masquer/afficher les objets identiques**  
Masquer les objets dans la liste si les métadonnées d’objet sont le même dans la base de données DB2 et dans SSMA.  
  
**Actualiser à partir de la base de données (flèche)**  
Utilisez le bouton fléché pour spécifier que les métadonnées pour les objets sélectionnés doivent être mis à jour dans SSMA.  
  
**Faire pas actualiser à partir de la base de données (bouton) X**  
Utilisez le bouton X pour spécifier que les métadonnées pour les objets sélectionnés ne doivent pas mis à jour dans SSMA.  
  
**Légende**  
Affiche un **légende** boîte de dialogue. La légende contient le mappage entre les couleurs de ligne et les États de métadonnées.  
  
Pour conserver le **légende** boîte de dialogue en haut de la **Actualiser à partir de la base de données** boîte de dialogue, sélectionnez le **afficher en haut** case à cocher.  
  
