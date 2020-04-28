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
ms.openlocfilehash: a53c3005aca2e599d8ceb0b973a58bcf2ca5e14c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68060127"
---
# <a name="refresh-from-database-db2tosql"></a>Actualiser à partir de la base de données (DB2ToSQL)
La boîte **de dialogue actualiser à partir de la base de données** vous permet de sélectionner les objets à actualiser à partir de la base de données DB2. Les lignes de la boîte de dialogue sont codées par couleur en fonction de l’état des métadonnées :  
  
-   Si les métadonnées de l’objet ont été modifiées localement et dans la base de données DB2, la ligne est bleue.  
  
-   Si les métadonnées de l’objet ont été modifiées dans la base de données DB2 mais pas dans SSMA, la ligne est en jaune.  
  
-   Si les métadonnées de l’objet ont été modifiées localement, mais pas dans la base de données DB2, la ligne est verte.  
  
-   Si l’objet est nouveau dans la base de données DB2, la ligne est rose.  
  
Vous pouvez spécifier les paramètres d’actualisation des objets par défaut dans la boîte de dialogue **paramètres du projet** . Pour plus d’informations, consultez [paramètres du projet&#40;synchronisation&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md).  
  
Pour accéder à la boîte **de dialogue actualiser à partir de la base de données** , cliquez avec le bouton droit sur un objet dans l’Explorateur de MÉTADONNÉEs DB2, puis cliquez sur **Actualiser dans**  
  
## <a name="options"></a>Options  
**Réduire (-)**  
Réduisez tous les groupes d’objets pour masquer des objets individuels.  
  
**Développer (+)**  
Développez tous les groupes d’objets pour afficher des objets individuels.  
  
**Masquer/afficher les objets égaux**  
Masque les objets de la liste si les métadonnées de l’objet sont identiques dans la base de données DB2 et dans SSMA.  
  
**Actualiser à partir de la base de données (bouton fléché)**  
Utilisez le bouton fléché pour spécifier que les métadonnées des objets sélectionnés doivent être mises à jour dans SSMA.  
  
**Ne pas actualiser à partir de la base de données (bouton X)**  
Utilisez le bouton X pour spécifier que les métadonnées des objets sélectionnés ne doivent pas être mises à jour dans SSMA.  
  
**Légende**  
Affiche une boîte de dialogue **légende** . La légende contient le mappage entre les couleurs des lignes et les États des métadonnées.  
  
Pour conserver la boîte de dialogue **légende** au-dessus de la boîte de dialogue **Actualiser à partir de la base de données** , activez la case à cocher Afficher par- **dessus** .  
  
