---
title: Se connecter à Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- instances of Analysis Services, connections
ms.assetid: 73ee8171-3379-4384-bfc8-071b3eebbc8f
author: minewiskan
ms.author: owend
ms.openlocfilehash: a019de00f932a8992b9adde426d1b9d953acb49f
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544011"
---
# <a name="connect-to-analysis-services"></a>Se connecter à Analysis Services
  Utilisez les informations de cette section pour en savoir plus sur les propriétés de chaîne de connexion, les bibliothèques clientes utilisées pour les connexions, les méthodes d'authentification prises en charge par Analysis Services et la procédure permettant de définir ou supprimer les connexions avant de déconnecter un serveur.  
  
## <a name="analysis-services-connections"></a>Connexions Analysis Services  
 Analysis Services utilise TCP comme protocole réseau et XML for Analysis (XMLA) comme protocole de communication. Au niveau le plus bas, toutes les bibliothèques clientes fournies avec Analysis Services implémentent XMLA sur TCP. Bien qu'il soit possible de créer des applications basées sur le format XMLA brut, la plupart des applications et des développeurs d'applications utilisent les bibliothèques clientes pour tirer parti des modèles objets et de l'efficacité de programmation qu'elles apportent. Pour les connexions du client à Analysis Services, vous pouvez vous servir d'IIS comme connexion intermédiaire si vous ne pouvez pas utiliser TCP dans la pile. Un des avantages de l'accès HTTP via IIS est la possibilité de se connecter à partir d'applications transmettant les informations d'identification dans la chaîne de connexion.  
  
 Toute discussion impliquant la connectivité inclut généralement l'authentification. Contrairement à d'autres fonctionnalités SQL Server, Analysis Services utilise exclusivement les informations d'identification Windows. Vous ne pouvez pas utiliser l'authentification de base de données SQL Server, l'authentification basée sur les revendications, l'authentification basée sur les formulaires ou l'authentification de type digest sur la connexion principale à Analysis Services. D'autres informations sur l'authentification sont fournies dans cette section.  
  
##  <a name="connection-tasks"></a><a name="bkmk_clientApps"></a>Tâches de connexion  
  
|Lien|Description de la tâche|  
|----------|----------------------|  
|[Connexion à partir d’applications clientes &#40;Analysis Service&#41;](connect-from-client-applications-analysis-services.md)|Si vous débutez avec Analysis Services, lisez cette rubrique pour commencer à utiliser les outils et les applications les plus courants avec Analysis Services.|  
|[Propriétés des chaînes de connexion &#40;Analysis Services&#41;](connection-string-properties-analysis-services.md)|Analysis Services inclut de nombreuses propriétés de serveur et de base de données, vous permettant de personnaliser une connexion à une application spécifique, indépendamment de la façon dont l'instance ou la base de données est configurée.|  
|[Méthodologies d'authentification prises en charge par Analysis Services](authentication-methodologies-supported-by-analysis-services.md)|Cette rubrique constitue une brève introduction aux méthodes d'authentification utilisées par Analysis Services.|  
|[Configurer Analysis Services pour la délégation contrainte Kerberos](configure-analysis-services-for-kerberos-constrained-delegation.md)|De nombreuses solutions de décisionnel nécessitent l'emprunt d'identité pour garantir que seules des données autorisées sont retournées pour chaque utilisateur. Dans cette rubrique, découvrez les conditions spécifiques à l'utilisation de l'emprunt d'identité. Cette rubrique décrit également les étapes de configuration d'Analysis Services pour la délégation contrainte Kerberos.|  
|[Inscription du nom SPN pour une instance Analysis Services](spn-registration-for-an-analysis-services-instance.md)|L'authentification Kerberos requiert un nom de principal du service (SPN) valide pour les services qui empruntent ou délèguent des identités d'utilisateur dans des solutions à plusieurs serveurs. Utilisez les informations de cette rubrique pour découvrir la construction et les étapes de l'inscription du SPN pour Analysis Services.|  
|[Configurer l’accès HTTP à Analysis Services sur Internet Information Services &#40;IIS&#41; 8.0](configure-http-access-to-analysis-services-on-iis-8-0.md)|L'authentification de base ou les limites interdomaines sont deux raisons importantes pour configurer Analysis Services pour l'accès HTTP.|  
|[Fournisseurs de données utilisés pour les connexions Analysis Services](data-providers-used-for-analysis-services-connections.md)|Analysis Services fournit trois bibliothèques clientes pour l'accès aux données Analysis Services ou aux opérations de serveur. Cette rubrique constitue une brève introduction aux objets ADOMD.NET, AMO (Analysis Services Management Objects) et au fournisseur OLE DB d'Analysis Services (MSOLAP).|  
|[Déconnecter des utilisateurs et sessions sur un serveur Analysis Services](disconnect-users-and-sessions-on-analysis-services-server.md)|Désactivez les sessions et les connexions existantes avant de mettre un serveur hors ligne ou d'effectuer des tests de performance de base.|  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;de configuration postérieures à l’installation Analysis Services&#41;](post-install-configuration-analysis-services.md)   
 [Configurer les propriétés du serveur dans Analysis Services](../server-properties/server-properties-in-analysis-services.md)   
 [Tâches d'administration à l'aide de scripts dans Analysis Services]](../script-administrative-tasks-in-analysis-services.md)  
  
  
