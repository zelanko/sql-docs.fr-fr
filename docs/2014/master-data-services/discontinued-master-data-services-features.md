---
title: Fonctionnalités de Master Data Services abandonnées dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3236cce0-cfd9-43f8-8be3-e8c8dff8f162
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ba09ba6110f5da2082f13d8277a00bfb9d590d2e
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84961919"
---
# <a name="discontinued-master-data-services-features-in-sql-server-2014"></a>Fonctionnalités Master Data Services supprimées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] qui ne sont plus disponibles dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="sssql14-discontinued-features"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] supprimées  
 Il n'y a pas de fonctionnalités supprimées dans cette version.  
  
## <a name="sssql11-discontinued-features"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] supprimées  
  
### <a name="security"></a>Sécurité  
 Pour faciliter la sécurité d'attribution, vous ne pouvez plus affecter des autorisations d'objet de modèle aux objets de hiérarchie dérivée, de hiérarchie explicite et de groupe d'attributs.  
  
-   Les autorisations de hiérarchie dérivée sont désormais basées sur le modèle. Par exemple, si vous souhaitez qu’un utilisateur dispose d’une autorisation sur une hiérarchie dérivée, vous devez affecter la **mise à jour** à l’objet de modèle. Vous pouvez ensuite affecter **refuser** l’accès à toutes les entités auxquelles vous ne voulez pas que l’utilisateur ait accès.  
  
-   Les autorisations de hiérarchie explicite sont maintenant basées sur l'entité. Par exemple, si l’utilisateur dispose d’autorisations de **mise à jour** sur une entité de compte, toutes les hiérarchies explicites de l’entité pourront être mises à jour.  
  
-   Les autorisations de groupe d’attributs ne peuvent plus être affectées dans la zone fonctionnelle **autorisations d’accès** . Au lieu de cela, dans la zone fonctionnelle **administration de système** où les groupes d’attributs sont créés, les utilisateurs et les groupes peuvent disposer de l’autorisation **mettre à jour** sur les groupes d’attributs. L’autorisation **en lecture seule sur les** groupes d’attributs n’est plus disponible.  
  
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
 Les règles d'entreprise qui génèrent automatiquement des valeurs pour l'attribut Code sont maintenant administrées différemment. Auparavant, pour générer des valeurs pour l’attribut code, vous avez utilisé l' **attribut default à une action valeur générée** dans la zone fonctionnelle **administration de système** sous **règles d’entreprise**. Désormais, dans **administration de système**, vous devez modifier l’entité pour activer les valeurs de code générées automatiquement. Pour plus d’informations, consultez [création automatique de Code &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).  
  
 Si vous possédez un package de déploiement de modèle [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] qui contient une règle de ce type, lorsque vous mettez à niveau la base de données vers [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], la règle d'entreprise est exclue.  
  
### <a name="bulk-updates-and-exporting"></a>Mises à jour et exporations en bloc  
 Dans l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], vous ne pouvez plus mettre à jour les valeurs d'attribut de plusieurs membres en bloc. Pour effectuer des mises à jour en bloc, utilisez le processus de site ou [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] .  
  
 Dans l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], vous ne pouvez plus exporter des membres vers Excel. Pour travailler avec des membres dans Excel, utilisez le [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] .  
  
### <a name="transactions"></a>Transactions  
 Dans la zone fonctionnelle **Explorateur** , les utilisateurs ne peuvent plus restaurer leurs propres transactions. Auparavant, les utilisateurs pouvaient annuler les modifications apportées aux données dans l' **Explorateur**. Les administrateurs peuvent toujours rétablir des transactions pour tous les utilisateurs dans la zone fonctionnelle **gestion des versions** .  
  
 Les annotations sont maintenant permanentes et ne peuvent pas être supprimées. Précédemment, les annotations étaient considérées comme des transactions et pouvaient être supprimées en inversant la transaction.  
  
### <a name="web-service"></a>Service Web  
 Le service Web de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est maintenant activé automatiquement, conformément aux exigences de Silverlight. Précédemment, le service Web devait être activé manuellement.  
  
### <a name="powershell-cmdlets"></a>Applets de commande Powershell  
 MDS n'inclut plus les applets de commande PowerShell.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités Master Data Services déconseillées dans SQL Server 2014](deprecated-master-data-services-features.md)  
  
  
