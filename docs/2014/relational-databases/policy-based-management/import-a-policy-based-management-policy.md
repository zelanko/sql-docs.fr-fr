---
title: Importer une stratégie de gestion basée sur des stratégies | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e4978471f25c1bf38d841e11f560a6bd99dac53e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62705314"
---
# <a name="import-a-policy-based-management-policy"></a>Importer une stratégie de gestion basée sur des stratégies
  Cette rubrique explique comment importer une instance de stratégie de gestion basée sur des stratégies dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour importer une instance de stratégie à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est fourni avec des stratégies qui peuvent être utilisées pour contrôler une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, ces stratégies ne sont pas installées sur le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], mais elles peuvent être importées à partir de l'emplacement par défaut C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-import-a-policy-instance"></a>Pour importer une instance de stratégie  
  
1.  Dans **l’Explorateur d’objets**, cliquez sur le signe plus (+) pour développer le serveur où l’instance de stratégie importée résidera.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez avec le bouton droit sur le dossier **Stratégies** et sélectionnez **Importer une stratégie**.  
  
5.  Dans la boîte de dialogue **Importer** , tapez le nom et le chemin du fichier ou utilisez le bouton Parcourir ( **...** ) pour rechercher et sélectionner le fichier XML qui contient la stratégie. Pour plus d'informations sur les options disponibles dans la boîte de dialogue **Importer** , consultez [Import Policies Dialog Box](import-policies-dialog-box.md).  
  
6.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
