---
title: Service de capture de données modifiées pour Oracle par Attunity | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a01524acf4fc72cb50732650f1f2e6f58b4ff74d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62771525"
---
# <a name="change-data-capture-service-for-oracle-by-attunity"></a>Service de capture de données modifiées pour Oracle par Attunity
  Le service de capture de données modifiées pour Oracle est un service Windows qui analyse les journaux des transactions Oracle et capture les modifications des tables d'intérêt dans des tables de modifications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les tables de modifications SQL dans lesquelles les modifications capturées à partir d'Oracle sont stockées sont du même type que les tables de modifications utilisées dans les fonctionnalités de capture de données modifiées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] natif. Cela rend la consommation de ces modifications aussi simple que la consommation des modifications apportées aux bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="installation"></a>Installation  
 Le service de capture de données modifiées pour Oracle peut être installé sur un ordinateur Windows pris en charge doté d'un accès à la base de données Oracle source qui est capturée et à l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible où la base de données CDC cible réside. Le service de capture de données modifiées n'a pas besoin d'une installation locale de la base de données Oracle ou de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , uniquement de leurs clients pris en charge. Pour plus d'informations sur l'emplacement d'installation des composants de base de données requis, consultez **Composants requis pour la base de données** dans cette rubrique.  
  
 L'installation du service de capture de données modifiées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour Oracle place l'interface de configuration du service et le programme de service dans l'emplacement sélectionné. Le service de capture de données modifiées pour Oracle est configuré séparément à l'aide de la console de configuration du service de capture de données modifiées Oracle. Pour plus d'informations sur la configuration du service de capture de données modifiées Oracle, consultez [Aide sur le service de capture de données modifiées pour Oracle par Attunity via la touche F1](change-data-capture-service-for-oracle-by-attunity-f1-help.md).  
  
 Pour installer le service de capture de données modifiées pour Oracle, exécutez manuellement **AttunityOracleCdcService.msi** à partir du support d'installation de SQL Server. Packages d’installation pour x86 et x64 se trouvent dans **.\Tools\AttunityCDCOracle\\**  sur le support d’installation de SQL Server.  
  
 Le service de capture de données modifiées pour Oracle peut être installé sur un ordinateur Windows pris en charge lorsque [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client est installé ; il n'a pas besoin d'être installé sur le même ordinateur où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible est installé.  
  
## <a name="supported-windows-environments"></a>Environnements Windows pris en charge  
 Le service de capture de données modifiées pour Oracle par Attunity s'exécute dans les environnements Windows suivants :  
  
-   Windows 8  
  
-   Windows 7 32 bits (x86) et 64 bits (x64)  
  
-   Windows Server 2012  
  
-   Windows Server 2008 R2 avec Service Pack 1  
  
-   Windows Server 2008 32 bits (x86) et 64 bits (x64) avec Service Pack 2  
  
## <a name="database-prerequisites"></a>Composants requis pour la base de données  
 Pour utiliser le service de capture de données modifiées pour Oracle, vous devez installer le logiciel [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle. Il s'agit d'un composant requis qui doit être obtenu auprès d'Oracle et installé avant d'installer le service de capture de données modifiées Oracle. En outre, vous devez installer le client SQL Server ODBC à l'aide du programme d'installation de SQL Server.  
  
 Le service de capture de données modifiées pour Oracle prend en charge les versions suivantes :  
  
### <a name="source-oracle-database"></a>Base de données Oracle source  
  
-   Base de données Oracle 11x (toute version)  
  
-   Base de données Oracle 10x (toute version)  
  
### <a name="target-sql-server-database"></a>Base de données SQL Server cible  
 Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="running-the-installation-program"></a>Exécution du programme d'installation  
 Pour installer le service de capture de données modifiées pour Oracle, ouvrez l'Assistant Installation de la plateforme Windows que vous utilisez (32/64 bit) et suivez les instructions à l'écran.  
  
## <a name="uninstalling-change-data-capture-service-for-oracle-by-attunity"></a>Désinstallation du service de capture de données modifiées pour Oracle par Attunity  
 Vous désinstallez le service de capture de données modifiées pour Oracle à l'aide du composant Programmes et fonctionnalités du Panneau de configuration.  
  
 La désinstallation du service de capture de données modifiées ne supprime pas les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créées. Pour la suppression complète de l'outil, vous devez supprimer la base de données MSXDBCDC et les bases de données CDC spécifiques qui ont été créés dans l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible que vous utilisez.  
  
 Si vous désinstallez le logiciel de service de capture de données modifiées d'un ordinateur et l'installez sur un autre ordinateur, vous devez uniquement fournir les définitions suivantes :  
  
-   Compte de service  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Chaîne de connexion et informations d’identification  
  
-   Mot de passe principal  
  
 Toutes les autres définitions sont stockées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et sont fournies par l'installation précédente sur un autre ordinateur.  
  
## <a name="in-this-documentation"></a>Dans cette documentation  
  
-   [Architecture système du service de capture de données modifiées pour Oracle par Attunity](change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [Service de capture de données modifiées Oracle](the-oracle-cdc-service.md)  
  
-   [Aide (F1) du service CDC pour Oracle par Attunity](change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [Service de capture de données modifiées pour Oracle par Attunity : rubrique Procédures](change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du service CDC Oracle](working-with-the-oracle-cdc-service.md)  
  
  
