---
title: Master Data Services fonctionnalités abandonnées dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3236cce0-cfd9-43f8-8be3-e8c8dff8f162
caps.latest.revision: 12
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f2e9a15b4a0f1441d63ab39a4b65861fcfef099e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167050"
---
# <a name="discontinued-master-data-services-features-in-sql-server-2014"></a>Fonctionnalités Master Data Services supprimées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] qui ne sont plus disponibles dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="includesssql14includessssql14-mdmd-discontinued-features"></a>Fonctionnalités [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] supprimées  
 Il n'y a pas de fonctionnalités supprimées dans cette version.  
  
## <a name="includesssql11includessssql11-mdmd-discontinued-features"></a>Fonctionnalités [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] supprimées  
  
### <a name="security"></a>Sécurité  
 Pour faciliter la sécurité d'attribution, vous ne pouvez plus affecter des autorisations d'objet de modèle aux objets de hiérarchie dérivée, de hiérarchie explicite et de groupe d'attributs.  
  
-   Les autorisations de hiérarchie dérivée sont désormais basées sur le modèle. Par exemple, si vous souhaitez un utilisateur soit autorisé à une hiérarchie dérivée, vous devez affecter **mise à jour** sur l’objet modèle. Vous pouvez alors assigner **Deny** accès à toutes les entités vous ne souhaitez pas que l’utilisateur ait accès.  
  
-   Les autorisations de hiérarchie explicite sont maintenant basées sur l'entité. Par exemple, si l’utilisateur a **mise à jour** autorisations à une entité de compte, puis toutes les hiérarchies explicites pour l’entité seront mises à jour.  
  
-   Autorisations de groupe d’attribut n’est plus peuvent être assignées dans le **autorisations d’accès** zone fonctionnelle. Au lieu de cela, dans le **Administration système** zone fonctionnelle où les groupes d’attributs sont créés, les utilisateurs et groupes peuvent être données **mise à jour** autorisation aux groupes d’attributs. **En lecture seule** autorisation aux groupes d’attributs n’est plus disponible.  
  
### <a name="staging-process"></a>Processus de site  
 Vous ne pouvez pas utiliser le nouveau processus de site pour effectuer les opérations suivantes :  
  
-   créer ou supprimer des collections ;  
  
-   ajouter des membres à des collections ou en supprimer ;  
  
-   réactiver des membres et des collections.  
  
 Vous pouvez vous servir du processus de site [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] pour utiliser des collections.  
  
### <a name="model-deployment-wizard"></a>Assistant Déploiement de modèle  
 Les packages qui contiennent des données ne peuvent plus être créés et déployés à l'aide de l'Assistant dans l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Un nouvel utilitaire de ligne de commande peut être utilisé à la place. Pour plus d’informations, consultez [Déploiement de modèles &#40;Master Data Services&#41;](deploying-models-master-data-services.md).  
  
 L'Assistant peut toujours être utilisé pour créer et déployer des packages qui ne contiennent pas de données.  
  
 En outre, les packages peuvent être déployés uniquement dans l'édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dans laquelle ils ont été créés. Cela signifie que les packages créés dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ne peuvent pas être déployés sur [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. Vous devez déployer le package dans un environnement [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] puis mettre à niveau la base de données vers [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
### <a name="code-generation-business-rules"></a>Règles d'entreprise de génération de code  
 Les règles d'entreprise qui génèrent automatiquement des valeurs pour l'attribut Code sont maintenant administrées différemment. Auparavant, pour générer des valeurs pour l’attribut Code, vous avez utilisé le **attribut par défaut avec une valeur générée** action dans le **Administration système** zone fonctionnelle sous **des règles d’entreprise** . Maintenant, dans **Administration système**, vous devez modifier l’entité pour activer les valeurs de Code générées automatiquement. Pour plus d’informations, consultez [Création automatique de code &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).  
  
 Si vous possédez un package de déploiement de modèle [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] qui contient une règle de ce type, lorsque vous mettez à niveau la base de données vers [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], la règle d'entreprise est exclue.  
  
### <a name="bulk-updates-and-exporting"></a>Mises à jour et exporations en bloc  
 Dans l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], vous ne pouvez plus mettre à jour les valeurs d'attribut de plusieurs membres en bloc. Pour effectuer des mises à jour en bloc, utilisez le processus de site ou le [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].  
  
 Dans l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], vous ne pouvez plus exporter des membres vers Excel. Pour travailler avec les membres dans Excel, utilisez le [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].  
  
### <a name="transactions"></a>Transactions  
 Dans le **Explorer** zone fonctionnelle, les utilisateurs ne peuvent plus restaurer leurs propres transactions. Auparavant, les utilisateurs pouvaient annuler les modifications apportées aux données dans **Explorer**. Les administrateurs peuvent toujours restaurer les transactions pour tous les utilisateurs dans le **gestion des versions** zone fonctionnelle.  
  
 Les annotations sont maintenant permanentes et ne peuvent pas être supprimées. Précédemment, les annotations étaient considérées comme des transactions et pouvaient être supprimées en inversant la transaction.  
  
### <a name="web-service"></a>Service Web  
 Le service Web de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est maintenant activé automatiquement, conformément aux exigences de Silverlight. Précédemment, le service Web devait être activé manuellement.  
  
### <a name="powershell-cmdlets"></a>Applets de commande Powershell  
 MDS n'inclut plus les applets de commande PowerShell.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités dépréciées de Master Data Services dans SQL Server 2014](deprecated-master-data-services-features.md)  
  
  
