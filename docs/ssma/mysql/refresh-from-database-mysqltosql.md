---
title: Actualiser à partir de la base de données (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 59a6db8f-2db6-4071-9005-928a7231de92
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: a3ca412381cf31edce8cf735fab630a6db92e5df
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935163"
---
# <a name="refresh-from-database-mysqltosql"></a>Actualiser à partir de la base de données (MySQLToSQL)
La boîte **de dialogue actualiser à partir de la base de données** vous permet de sélectionner les objets à actualiser à partir de la base de données MySQL. Les lignes de la boîte de dialogue sont codées par couleur en fonction de l’état des métadonnées :  
  
-   Si les métadonnées de l’objet ont été modifiées localement et dans la base de données MySQL, la ligne est bleue.  
  
-   Si les métadonnées de l’objet ont été modifiées dans la base de données MySQL, mais pas dans SSMA, la ligne est en jaune.  
  
-   Si les métadonnées de l’objet ont été modifiées localement, mais pas dans la base de données MySQL, la ligne est verte.  
  
-   Si l’objet est nouveau dans la base de données MySQL, la ligne est rose.  
  
Vous pouvez spécifier les paramètres d’actualisation des objets par défaut dans la boîte de dialogue **paramètres du projet** . Pour plus d’informations, consultez [paramètres du projet &#40;synchronisation&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md)  
  
Pour accéder à la boîte **de dialogue actualiser à partir de la base de données** , cliquez avec le bouton droit sur un objet dans l’Explorateur de métadonnées MySQL, puis cliquez sur **Actualiser à partir**  
  
## <a name="options"></a>Options  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Réduire (-)**|Réduisez tous les groupes d’objets pour masquer des objets individuels.|  
|**Développer (+)**|Développez tous les groupes d’objets pour afficher des objets individuels.|  
|**Masquer/afficher les objets égaux**|Masque les objets de la liste si les métadonnées de l’objet sont identiques dans la base de données MySQL et dans SSMA.|  
|**Actualiser à partir de la base de données (bouton fléché)**|Utilisez le bouton fléché pour spécifier que les métadonnées des objets sélectionnés doivent être mises à jour dans SSMA.|  
|**Ne pas actualiser à partir de la base de données (bouton X)**|Utilisez le bouton X pour spécifier que les métadonnées des objets sélectionnés ne doivent pas être mises à jour dans SSMA.|  
|**Légende**|Affiche une boîte de dialogue **légende** . La légende contient le mappage entre les couleurs des lignes et les États des métadonnées.<br /><br />Pour conserver la boîte de dialogue **légende** au-dessus de la boîte de dialogue **Actualiser à partir de la base de données** , activez la case à cocher Afficher par- **dessus** .|  
  
