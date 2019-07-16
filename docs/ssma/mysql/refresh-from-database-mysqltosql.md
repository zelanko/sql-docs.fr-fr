---
title: Actualiser à partir de la base de données (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 59a6db8f-2db6-4071-9005-928a7231de92
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5acc3153d7305f404c5fc6a0478b83cc0c98bad6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68066705"
---
# <a name="refresh-from-database-mysqltosql"></a>Actualiser à partir de la base de données (MySQLToSQL)
Le **Actualiser à partir de la base de données** boîte de dialogue vous permet de sélectionner les objets à actualiser à partir de la base de données MySQL. Lignes dans la boîte de dialogue sont codées par couleur selon l’état des métadonnées :  
  
-   Si les métadonnées de l’objet a été modifié localement et dans la base de données MySQL, la ligne est bleu.  
  
-   Si les métadonnées de l’objet a changé dans la base de données MySQL, mais pas dans SSMA, la ligne est jaune.  
  
-   Si les métadonnées de l’objet a été modifié localement, mais pas dans la base de données MySQL, la ligne est vert.  
  
-   Si l’objet est nouveau dans la base de données MySQL, la ligne est rose.  
  
Vous pouvez spécifier des paramètres d’actualisation objet par défaut dans le **paramètres du projet** boîte de dialogue. Pour plus d’informations, consultez [paramètres du projet &#40;synchronisation&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md)  
  
Pour accéder à la **Actualiser à partir de la base de données** boîte de dialogue, avec le bouton droit, un objet dans l’Explorateur de métadonnées de MySQL et cliquez sur **Actualiser à partir de la base de données**.  
  
## <a name="options"></a>Options  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Réduction (-)**|Réduire tous les groupes d’objets pour masquer les objets individuels.|  
|**Développement (+)**|Développez tous les groupes d’objets pour afficher les objets individuels.|  
|**Masquer/afficher les objets identiques**|Masquer les objets dans la liste si les métadonnées d’objet sont le même dans la base de données MySQL et de SSMA.|  
|**Actualiser à partir de la base de données (flèche)**|Utilisez le bouton fléché pour spécifier que les métadonnées pour les objets sélectionnés doivent être mis à jour dans SSMA.|  
|**Faire pas actualiser à partir de la base de données (bouton) X**|Utilisez le bouton X pour spécifier que les métadonnées pour les objets sélectionnés ne doivent pas mis à jour dans SSMA.|  
|**Légende**|Affiche un **légende** boîte de dialogue. La légende contient le mappage entre les couleurs de ligne et les États de métadonnées.<br /><br />Pour conserver le **légende** boîte de dialogue en haut de la **Actualiser à partir de la base de données** boîte de dialogue, sélectionnez le **afficher en haut** case à cocher.|  
  
