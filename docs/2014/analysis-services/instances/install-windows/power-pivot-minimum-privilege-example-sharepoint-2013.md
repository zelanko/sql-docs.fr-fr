---
title: Exemple de Configuration avec privilèges Minimum pour PowerPivot pour SharePoint 2013 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c1e09e6c-52d3-48ab-8c70-818d5d775087
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec782dab7b86b17f06a22bebf2e8549a08a55085
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200339"
---
# <a name="example-of-a-minimum-privilege-configuration-for-powerpivot-for-sharepoint-2013"></a>Exemple de Configuration avec privilèges Minimum pour PowerPivot pour SharePoint 2013
  Cette rubrique décrit un exemple de configuration de PowerPivot pour SharePoint 2013 avec les privilèges minimums. La configuration utilise un compte différent pour chacun des trois composants et chaque compte dispose du niveau minimum de privilèges.  
  
## <a name="summary-of-accounts"></a>Récapitulatif des comptes  
 PowerPivot pour SharePoint 2013 prend en charge l'utilisation du compte Service réseau pour le compte de service Analysis Services. Le compte Service réseau n'est pas un scénario pris en charge avec SharePoint 2010. Pour plus d’informations sur les comptes de Service, consultez [configurer les comptes de Service Windows et les autorisations](http://msdn.microsoft.com/library/ms143504.aspx) (http://msdn.microsoft.com/library/ms143504.aspx).  
  
 Le tableau suivant récapitule les trois comptes utilisés dans cet exemple de configuration avec privilèges minimums.  
  
|Portée|Nom   |  
|-----------|----------|  
|Compte Administrateur SharePoint|**SPAdmin**|  
|Compte de batterie de serveurs SharePoint|**SPFarm**|  
|Compte de service Analysis Services|**SPsvc**|  
  
### <a name="the-sharepoint-administrator-account-spadmin"></a>Compte Administrateur SharePoint (SpAdmin)  
 **SPAdmin** est un compte de domaine que vous utilisez pour installer et configurer la batterie de serveurs. Il s’agit du compte utilisé pour exécuter l’Assistant Configuration SharePoint et l’outil de Configuration de PowerPivot pour SharePoint 2013 **SPAdmin** compte est le seul compte qui requiert des droits d’administrateur local. Avant d’exécuter l’outil de Configuration de PowerPivot, accordez le **SPAdmin** des privilèges à l’instance de base de données SQL Server où SharePoint crée les bases de données de contenu et la configuration du compte. Pour configurer le compte SPAdmin dans un scénario avec privilèges minimums, il doit être membre des rôles **securityadmin** et **dbcreator**.  
  
### <a name="the-farm-account-spfarm"></a>Compte de batterie de serveurs (SPFarm)  
 **SPFarm** est un compte de domaine que le service du minuteur SharePoint et l'application Web de l'Administration centrale utilisent pour accéder à la base de données de contenu SharePoint. Ce compte n'a pas besoin d'être administrateur local. L’Assistant Configuration SharePoint octroie le privilège minimal approprié dans la base de données SQL Server principale. La configuration de privilèges minimums SQL Server correspond à l’appartenance aux rôles **securityadmin** et **dbcreator**.  
  
### <a name="the-service-account-for-powerpivot-service-spsvc"></a>Compte de service pour le service PowerPivot (SPsvc)  
 Si une nouvelle batterie de serveurs SharePoint n'est pas configurée avant d'exécuter l'outil de configuration PowerPivot, alors, par défaut, l'outil de configuration PowerPivot crée ce qui suit :  
  
-   Application de service PowerPivot.  
  
-   Application Excel Services.  
  
-   Application Banque d'informations sécurisée.  
  
 L'outil de configuration PowerPivot configure les trois applications de service dans le pool d'applications par défaut. Ce pool d'applications est généralement configuré pour s'exécuter sous le compte SPFarm, lequel a accès à un grand nombre de ressources dont un compte de service n'a pas besoin. Pour transformer l'environnement en un environnement de privilèges minimums, configurez un nouveau compte de domaine qui sera utilisé par le pool d'applications et l'application Web appropriés.  
  
 **Pour créer un compte de domaine SPsvc à utiliser comme compte de service SharePoint :**  
  
1.  Dans Administration centrale de SharePoint, cliquez sur **sécurité**.  
  
2.  Cliquez sur **configurer des comptes de Service**  
  
3.  Cliquez sur **inscrire le nouveau compte géré**.  
  
 Le compte **SPSvc** ne dispose d'aucun privilège d'administrateur local et SPsvc ne disposera d'aucun privilège dans la base de données SharePoint. Seuls les privilèges requis par SPsvc sont les droits d'administration sur l'instance PowerPivot d'Analysis Services.  
  
 **Pour configurer le pool d'applications approprié pour utiliser le compte de SPsvc :**  
  
1.  Dans Administration centrale de SharePoint, cliquez sur **sécurité**.  
  
2.  Cliquez sur **configurer des comptes de Service**.  
  
3.  Sélectionnez le pool d'application de service utilisé par l'application de service PowerPivot. Ensuite, sélectionnez le compte SPSvc.  
  
 **Pour accorder l'accès à l'application Web avec PowerShell :**  
  
1.  Exécutez SharePoint 2013 Management Shell avec des privilèges d'administrateur.  
  
2.  Exécutez le code PowerShell suivant :  
  
    ```  
    $webApp = Get-SPWebApplication "http://<servername>"  
    $webApp.GrantAccessToProcessIdentity("DOMAIN\<ServiceAccountName>")  
  
    ```  
  
  
