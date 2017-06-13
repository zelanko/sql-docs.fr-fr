---
title: "Implémentation d’une classe de connexion pour une Extension de traitement de données | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- connections [Reporting Services], data processing extensions
- Connection class
- data processing extensions [Reporting Services], connections
ms.assetid: 7047d29e-a2c9-4e6f-ad02-635851a38ed7
caps.latest.revision: 42
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 1108be24704c38f0891e623fda02803e5f8c21e5
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="implementing-a-connection-class-for-a-data-processing-extension"></a>Implémentation d'une classe Connection pour une extension pour le traitement des données
  Le **connexion** objet représente une connexion de base de données ou d’une ressource similaire et est le point de départ pour les utilisateurs d’un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extension pour le traitement des données. Il représente les connexions aux serveurs de base de données, bien que toute entité ayant un comportement similaire peut être exposée comme un **connexion**.  
  
 Pour implémenter un **connexion** de l’objet, créez une classe qui implémente <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> et éventuellement implémente <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>.  
  
 Dans votre implémentation, vous devez garantir qu'une connexion est créée et ouverte avant que les commandes puissent être exécutées. Veillez à ce que votre implémentation oblige les clients à ouvrir et fermer des connexions explicitement, plutôt qu'une implémentation qui ouvre et ferme des connexions implicitement pour le client. Effectuez vos vérifications de la sécurité lorsque la connexion est obtenue. La nécessité d'une connexion existante pour les autres classes dans votre extension pour le traitement des données [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] garantit ensuite que les vérifications de la sécurité sont toujours effectuées lors de l'utilisation de votre source de données.  
  
 Les propriétés de la connexion souhaitée sont représentées sous la forme d'une chaîne de connexion. Il est fortement recommandé que les extensions pour le traitement des données [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] prennent en charge la propriété <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection.ConnectionString%2A> à l'aide du système de paire nom/valeur familier défini par OLE DB.  
  
> [!NOTE]  
>  **Connexion** objets sont souvent beaucoup de ressources pour obtenir, vous pouvez donc envisager de regrouper des connexions ou autres techniques pour atténuer ce risque.  
  
 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> hérite de <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Vous devez implémenter l'interface <xref:Microsoft.ReportingServices.Interfaces.IExtension> dans le cadre de votre implémentation de classe de connexion. L'interface <xref:Microsoft.ReportingServices.Interfaces.IExtension> permet à une classe d'implémenter un nom d'extension localisé et de traiter des informations de configuration spécifiques à l'extension stockées dans le fichier de configuration [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Votre **connexion** objet contient la <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A> propriété via son implémentation de <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Il est fortement recommandé que les extensions pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] prennent en charge la propriété <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A>, afin que les utilisateurs soient confrontés à un nom localisé familier pour l'extension dans une interface utilisateur, telle que Gestionnaire de rapports.  
  
 <xref:Microsoft.ReportingServices.Interfaces.IExtension>permet également de votre **connexion** objet pour récupérer et traiter les données de configuration personnalisées stockées dans le fichier RSReportServer.config. Pour plus d'informations sur le traitement des données de configuration personnalisées, consultez la méthode <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A>.  
  
 La classe qui implémente <xref:Microsoft.ReportingServices.Interfaces.IExtension> n'est pas déchargée de la mémoire lorsque vos classes restantes d'extension pour le traitement des données sont déchargées. Pour cette raison, vous pouvez utiliser votre **Extension** classe pour stocker les informations d’état de la connexion croisée ou pour stocker des données qui peuvent être mis en cache en mémoire. Votre **Extension** classe reste en mémoire tant que le serveur de rapports est en cours d’exécution.  
  
 Vous pouvez étendre votre **connexion** classe pour inclure la prise en charge des informations d’identification dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] en implémentant <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>. Lorsque vous implémentez le <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.IntegratedSecurity%2A>, <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.UserName%2A>, et <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.Password%2A> propriétés de la <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> interface, vous activez le **sécurité intégrée** case à cocher et **nom d’utilisateur** et **mot de passe** des zones de texte de la **Source de données** boîte de dialogue dans le Concepteur de rapports. Cette opération permet au Générateur de rapports de stocker et d'extraire des informations d'identification pour les sources de données qui prennent en charge l'authentification. Les informations d'identification sont stockées de manière sécurisée et utilisées lors du rendu des rapports en mode aperçu.  
  
> [!NOTE]  
>  L'implémentation implicite de <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> nécessite d'implémenter les membres des interfaces <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> et <xref:Microsoft.ReportingServices.Interfaces.IExtension>.  
>   
>  Pour obtenir un exemple **connexion** implémentation de la classe, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implémentation d’une Extension de traitement des données](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
