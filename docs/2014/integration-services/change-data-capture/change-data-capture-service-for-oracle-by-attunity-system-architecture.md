---
title: Architecture système de Change Data Capture Service pour Oracle d’Attunity | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1db6c737-3c60-4066-a0a3-3611e1c83e4e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e04a6a174143d2da6d85ae27dd84ecf516f533fa
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756879"
---
# <a name="change-data-capture-service-for-oracle-by-attunity-system-architecture"></a>Architecture système du service de capture de données modifiées pour Oracle par Attunity
  Le service de capture de données modifiées pour Oracle capture les modifications apportées aux tables sélectionnées dans une ou plusieurs bases de données Oracle sources dans les bases de données CDC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] situées sur une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Le diagramme suivant montre les composants qui composent le service de capture de données modifiées pour Oracle.  
  
 ![Architecture du service](../media/service-architecture.gif "Architecture du service")  
  
 Cette illustration montre quatre plateformes utilisées. Dans de nombreux cas, ces plateformes peuvent se chevaucher, mais ce schéma représente un cas de figure standard. Par exemple, il est logique que les bases de données Oracle et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] s'exécutent chacune sur un ordinateur différent et ne soient pas partagées avec la plateforme de service de capture de données modifiées Oracle ou la plateforme à partir de laquelle le service de capture de données modifiées est conçu. Les plateformes illustrées sont les suivantes :  
  
-   Le Service de capture de données modifiées Oracle : Cela peut être n’importe quel ordinateur Windows pris en charge, où le Service de capture de données modifiées Oracle est installé et exécuté. Cette plateforme peut également représenter un nœud de cluster dans un cluster de basculement Microsoft (les configurations de haute disponibilité sont présentées plus loin dans ce document).  
  
-   La base de données Oracle : Cela peut être n’importe quel ordinateur sur lequel s’exécute une version prise en charge de la base de données Oracle. Cela inclut tous les ordinateurs Windows, Linux ou exécutant tout autre système d'exploitation pris en charge par la version de la base de données Oracle installée. Notez que le diagramme affiche cette plateforme au pluriel parce qu'un seul service de capture de données modifiées Oracle peut capturer des modifications de plusieurs bases de données Oracle sources.  
  
-   Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Cela peut être n’importe quel ordinateur où la cible [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] base de données (une référence (SKU) prises en charge de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]) s’exécute. Un service de capture de données modifiées Oracle prend en charge une cible [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] où il stocke les tables de modifications et la configuration du service. La plateforme [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut également représenter une instance en cluster de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ou une instance en miroir de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de la fonctionnalité **AlwaysOn** .  
  
-   Le Concepteur de capture de données modifiées Oracle : Cela peut être n’importe quel ordinateur Windows pris en charge qui peut accéder à la base de données Oracle source et la cible [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] base de données.  
  
 Le tableau suivant décrit les composants qui s'exécutent sur l'une des quatre plateformes décrites ci-dessus.  
  
|Composant/Description|Le composant comprend :|  
|----------------------------|----------------------------|  
|Service de capture de données modifiées Oracle : Il s’agit d’un service Windows où l’activité de capture de données modifiées a lieu.|Instance Oracle CDC : Un sous-processus du Service de capture de données modifiées Oracle poignées permettent de modifier activité de capture de données pour une base de données Oracle source unique (il existe une seule instance Oracle CDC par base de données source Oracle).<br /><br /> Lecture du journal Oracle : Lit les journaux des transactions Oracle à l’aide du Client Oracle.<br /><br /> Client Oracle : Oracle Instant Client utilisé pour la communication avec Oracle. Il s'agit d'un composant requis qui doit être obtenu auprès d'Oracle et installé avant d'installer le service de capture de données modifiées Oracle.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Enregistreur des modifications : Écrit les modifications validées apportées à la table Oracle capturée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]tables de modifications. Ce composant conserve également cet état de capture dans la base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cible.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Client ODBC : Le Client natif de Microsoft pour [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Il s'agit d'un composant requis qui doit être obtenu auprès de Microsoft et installé avant d'installer le service de capture de données modifiées Oracle.|  
|Configuration du Service de capture de données modifiées Oracle : Ceci est un composant logiciel enfichable Microsoft Management Console qui crée le service Windows et installe sa configuration.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client : Le client SQL ADO.NET fourni avec la version 4 du .NET framework.|  
|Base de données Oracle : Une base de données Oracle source à partir de quelles modifications pour sélectionner des tables sont capturées.|Log Miner : Un composant Oracle par le biais duquel les journaux des transactions Oracle sont lus.<br /><br /> Journaux des transactions : L’en ligne et archivés Oracle de restauration par progression les journaux qui sont utilisés par Oracle pour vous assurer que la base de données peut avoir un impact sauvegarder des transactions et récupérer après des défaillances (dans ce cas, il s’agit de l’Oracle de base de données doit fonctionner en mode archivelog).|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance : Un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance où se trouvent les bases de données de capture de données modifiées. Il peut s'agir d'une instance en cluster [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (cluster de basculement) ou d'une base de données mise en miroir (AlwaysOn).|La base de données MSXDBCDC : Une base de données où plus d’informations sur les Services de capture de données modifiées utilisant ce [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance est conservée. Elle conserve également des informations sur les instances Oracle CDC gérées par chaque service de capture de données modifiées. Cette base de données est créée dans le cadre du processus de création du service de capture de données modifiées.<br /><br /> Bases de données CDC : bases de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui stockent les modifications apportées à l'une des bases de données Oracle sources. Les bases de données CDC étant activées pour la capture de données modifiées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , elles possèdent des tables et des fonctions de capture de données modifiées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , ce qui facilite la consommation de modifications provenant d'Oracle.|  
|Concepteur de capture de données modifiées Oracle : Un composant logiciel enfichable Microsoft Management Console permet de créer des Instances de capture de données modifiées Oracle. Utilisez ce composant pour sélectionner les tables et les colonnes à capturer, fournir les informations de connexion Oracle et gérer le cycle de vie des instances de capture de données modifiées.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client : Le client SQL ADO.NET fourni avec la version 4 du .NET framework.<br /><br /> Client Oracle : Oracle Instant Client utilisé pour la communication avec Oracle. Il s'agit d'un composant requis qui doit être obtenu auprès d'Oracle et installé avant d'installer le service de capture de données modifiées Oracle.|  
  
 Le service de capture de données modifiées Oracle et ses instances Oracle CDC enfants ne peuvent communiquer qu'avec la ou les bases de données Oracle sources et l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cible comme clients. Ils n'écoutent pas activement le réseau et d'autres protocoles. Le service de capture de données modifiées Oracle surveille les modifications de configuration apportées aux bases de données CDC et met à jour son exécution selon la configuration mise à jour.  
  
  
