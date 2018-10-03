---
title: Modifier une alerte de données dans le Concepteur d’alertes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- editing, data alerts
- updating, data alerts
- editing, alerts
- updating, alerts
ms.assetid: dde3664d-90b5-4b12-969e-39152c86e58a
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 511a057721f1dbd8273fe1909c4eaae31dd128f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119439"
---
# <a name="edit-a-data-alert-in-alert-designer"></a>Modifier une alerte de données dans le Concepteur d'alertes
  Vous ouvrez la définition d'alerte de données que vous souhaitez modifier dans le Gestionnaire des alertes de données. Uniquement l'utilisateur qui a créé la définition d'alerte peut la modifier. Pour plus d’informations sur l’ouverture du Gestionnaire des alertes de données, consultez [Gérer mes alertes de données dans le Gestionnaire des alertes de données](manage-my-data-alerts-in-data-alert-manager.md).  
  
 L'image suivante montre le menu contextuel d'une alerte de données dans le Gestionnaire des alertes de données.  
  
 ![Ouvrir le Concepteur d’alertes de données en cliquant sur Modifier](media/rs-alertmanageriwopendesigner.gif "Ouvrir le Concepteur d’alertes de données en cliquant sur Modifier")  
  
 La procédure suivante décrit les étapes pour ouvrir la définition d'alerte et la modifier dans le Concepteur d'alertes de données du Gestionnaire des alertes de données.  
  
### <a name="to-edit-a-data-alert-definition-in-data-alert-designer"></a>Pour modifier une définition d'alerte de données dans le Concepteur d'alertes de données  
  
1.  Dans le Gestionnaire des alertes de données, cliquez avec le bouton droit sur la définition d’alerte de données à modifier, puis cliquez sur l’option **Modifier**.  
  
     La définition de l'alerte s'ouvre dans le Concepteur d'alertes de données.  
  
2.  Mettez à jour les règles, les paramètres de planification et les paramètres de courrier électronique. Pour plus d’informations, consultez [Concepteur d’alertes de données](../../2014/reporting-services/data-alert-designer.md) et [créer une alerte dans Concepteur d’alertes de données](create-a-data-alert-in-data-alert-designer.md).  
  
    > [!NOTE]  
    >  Vous ne pouvez pas choisir un flux de données différent. Si vous souhaitez utiliser un flux de données différent, vous devez créer une nouvelle définition d'alerte de données.  
  
3.  Cliquez sur **Enregistrer**.  
  
    > [!NOTE]  
    >  Si le rapport a changé et les flux de données générés à partir du rapport ont changé, la définition d'alerte peut ne plus être valide. Ceci se produit lorsqu'une colonne référencée par la définition d'alerte dans ses règles est supprimée du rapport, si le type de ses données change, ou encore, si le rapport est supprimé ou déplacé. Vous pouvez ouvrir une définition d'alerte non valide, mais vous ne pouvez pas l'enregistrer tant qu'elle n'est pas compatible avec la version actuelle du flux de données du rapport sur lequel elle repose. Pour en savoir plus sur la façon dont les flux de données sont générés à partir des rapports, consultez [Génération de flux de données à partir de rapports &#40;Générateur de rapports et SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire des alertes de données pour les administrateurs d’alertes](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)   
 [Alertes de données Reporting Services](../ssms/agent/alerts.md)  
  
  
