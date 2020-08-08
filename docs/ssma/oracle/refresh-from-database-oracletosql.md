---
title: Actualiser à partir de la base de données (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 84492f44-c368-4c75-954d-7307a2d2bbc0
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 694953d914b9811208f2ea143f93e2c91878f07b
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87933010"
---
# <a name="refresh-from-database-oracletosql"></a>Actualiser à partir de la base de données (OracleToSQL)
La boîte **de dialogue actualiser à partir de la base de données** vous permet de sélectionner les objets à actualiser à partir de la base de données Oracle. Les lignes de la boîte de dialogue sont codées par couleur en fonction de l’état des métadonnées :  
  
-   Si les métadonnées de l’objet ont été modifiées localement et dans la base de données Oracle, la ligne est bleue.  
  
-   Si les métadonnées de l’objet ont été modifiées dans la base de données Oracle, mais pas dans SSMA, la ligne est en jaune.  
  
-   Si les métadonnées de l’objet ont été modifiées localement, mais pas dans la base de données Oracle, la ligne est verte.  
  
-   Si l’objet est nouveau dans la base de données Oracle, la ligne est rose.  
  
Vous pouvez spécifier les paramètres d’actualisation des objets par défaut dans la boîte de dialogue **paramètres du projet** . Pour plus d’informations, consultez [paramètres du projet&#40;synchronisation&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
Pour accéder à la boîte **de dialogue actualiser à partir de la base de données** , cliquez avec le bouton droit sur un objet dans l’Explorateur de métadonnées Oracle, puis cliquez sur **Actualiser à partir**  
  
## <a name="options"></a>Options  
**Réduire (-)**  
Réduisez tous les groupes d’objets pour masquer des objets individuels.  
  
**Développer (+)**  
Développez tous les groupes d’objets pour afficher des objets individuels.  
  
**Masquer/afficher les objets égaux**  
Masque les objets de la liste si les métadonnées de l’objet sont identiques dans la base de données Oracle et dans SSMA.  
  
**Actualiser à partir de la base de données (bouton fléché)**  
Utilisez le bouton fléché pour spécifier que les métadonnées des objets sélectionnés doivent être mises à jour dans SSMA.  
  
**Ne pas actualiser à partir de la base de données (bouton X)**  
Utilisez le bouton X pour spécifier que les métadonnées des objets sélectionnés ne doivent pas être mises à jour dans SSMA.  
  
**Légende**  
Affiche une boîte de dialogue **légende** . La légende contient le mappage entre les couleurs des lignes et les États des métadonnées.  
  
Pour conserver la boîte de dialogue **légende** au-dessus de la boîte de dialogue **Actualiser à partir de la base de données** , activez la case à cocher Afficher par- **dessus** .  
  
