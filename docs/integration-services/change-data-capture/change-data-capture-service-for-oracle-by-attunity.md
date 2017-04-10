---
title: "Service de capture de donn&#233;es modifi&#233;es pour Oracle par Attunity | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Service de capture de donn&#233;es modifi&#233;es pour Oracle par Attunity
  Le service de capture de données modifiées pour Oracle est un service Windows qui analyse les journaux des transactions Oracle et capture les modifications des tables d'intérêt dans des tables de modifications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les tables de modifications SQL dans lesquelles les modifications capturées à partir d'Oracle sont stockées sont du même type que les tables de modifications utilisées dans les fonctionnalités de capture de données modifiées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] natif. Cela rend la consommation de ces modifications aussi simple que la consommation des modifications apportées aux bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Installation  
 Le service et le concepteur de capture de données modifiées Microsoft® pour Oracle par Attunity pour Microsoft SQL Server® 2016 font partie du Feature Pack de SQL Server 2016. Téléchargez les composants du Feature Pack à partir de la [page web SQL Server 2016 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=746297).  
  
 Le service de capture de données modifiées pour Oracle peut être installé sur un ordinateur Windows pris en charge doté d’un accès à la base de données Oracle source qui est capturée et à l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible où la base de données CDC cible réside. Le service de capture de données modifiées n'a pas besoin d'une installation locale de la base de données Oracle ou de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , uniquement de leurs clients pris en charge. Pour plus d'informations sur l'emplacement d'installation des composants de base de données requis, consultez **Composants requis pour la base de données** dans cette rubrique.  
  
 L'installation du service de capture de données modifiées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour Oracle place l'interface de configuration du service et le programme de service dans l'emplacement sélectionné. Le service de capture de données modifiées pour Oracle est configuré séparément à l'aide de la console de configuration du service de capture de données modifiées Oracle. Pour plus d'informations sur la configuration du service de capture de données modifiées Oracle, consultez [Change Data Capture Service for Oracle by Attunity F1 Help](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-f1-help.md).  
  
 Le service de capture de données modifiées pour Oracle peut être installé sur un ordinateur Windows pris en charge lorsque [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client est installé ; il n'a pas besoin d'être installé sur le même ordinateur où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible est installé.  
  
## Environnements Windows pris en charge  
 Le service de capture de données modifiées pour Oracle par Attunity s'exécute dans les environnements Windows suivants :  
  
-   Windows Vista avec Service Pack 2  
  
-   Windows 7  
  
-   Windows 8 et 8.1  
  
-   Windows 10  
  
-   Windows Server 2008 R2  
  
-   Windows Server 2008 avec Service Pack 2  
  
-   Windows Server 2012  
  
## Composants requis pour la base de données  
 Pour utiliser le service de capture de données modifiées pour Oracle, vous devez installer le logiciel [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle. Il s'agit d'un composant requis qui doit être obtenu auprès d'Oracle et installé avant d'installer le service de capture de données modifiées Oracle. En outre, vous devez installer le client SQL Server ODBC à l'aide du programme d'installation de SQL Server.  
  
 Le service de capture de données modifiées pour Oracle prend en charge les versions suivantes :  
  
### Base de données Oracle source  
  
-   Base de données Oracle 11x (toute version)  
  
-   Base de données Oracle 10x (toute version)  
  
-   Oracle Database 10g Version 2 : 10.2.0.1-10.2.0.5 (ensemble de correctifs à partir d'avril 2010)  
  
-   Oracle Database 11g Version 1 : 11.1.0.6-11.1.0.7 (ensemble de correctifs à partir de septembre 2008)  
  
-   Oracle Database 11g Version 2 : 11.2.0.1-11.2.0.3 (ensemble de correctifs à partir de septembre 2011)  

-   Oracle Database 12c en installation classique. (L’installation multi-locataire n’est pas prise en charge.)  
  
### Base de données SQL Server cible  
 Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
## Exécution du programme d'installation  
 Pour installer le service de capture de données modifiées pour Oracle, ouvrez l'Assistant Installation de la plateforme Windows que vous utilisez (32/64 bit) et suivez les instructions à l'écran.  
  
## Désinstallation du service de capture de données modifiées pour Oracle par Attunity  
 Vous désinstallez le service de capture de données modifiées pour Oracle à l'aide du composant Programmes et fonctionnalités du Panneau de configuration.  
  
 La désinstallation du service de capture de données modifiées ne supprime pas les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créées. Pour la suppression complète de l'outil, vous devez supprimer la base de données MSXDBCDC et les bases de données CDC spécifiques qui ont été créés dans l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible que vous utilisez.  
  
 Si vous désinstallez le logiciel de service de capture de données modifiées d'un ordinateur et l'installez sur un autre ordinateur, vous devez uniquement fournir les définitions suivantes :  
  
-   Compte de service  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Chaîne de connexion et informations d’identification  
  
-   Mot de passe principal  
  
 Toutes les autres définitions sont stockées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et sont fournies par l'installation précédente sur un autre ordinateur.  
  
## Dans cette documentation  
  
-   [Architecture système du service de capture de données modifiées pour Oracle par Attunity](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [Service de capture de données modifiées Oracle](../../integration-services/change-data-capture/the-oracle-cdc-service.md)  
  
-   [Aide sur le service de capture de données modifiées pour Oracle par Attunity via la touche F1](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [Service de capture de données modifiées pour Oracle par Attunity : rubrique Procédures](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## Voir aussi  
 [Utilisation du service de capture de données modifiées Oracle](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md)  
  
  