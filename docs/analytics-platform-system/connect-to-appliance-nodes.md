---
title: Se connecter aux nœuds de l’appliance
description: Cet article explique les différentes façons de se connecter à chaque nœud dans l’appliance Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: e1182d174e3281fda944c0b6490b114d4b6f2244
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401247"
---
# <a name="connect-to-appliance-nodes-in-analytics-platform-system"></a>Se connecter à des nœuds d’appliance dans Analytics Platform System
Cet article explique les différentes façons de se connecter à chaque nœud dans l’appliance Analytics Platform System.  
  
## <a name="connecting-with-hadoop"></a>Connexion avec Hadoop  
Avant d’utiliser Hadoop avec SQL Server PDW, demandez à l’administrateur de l’appareil d’installer le Java Runtime Environment sur SQL Server PDW. Pour obtenir des instructions, consultez [configurer la connectivité Polybase à des données externes &#40;Analytics Platform System&#41;](configure-polybase-connectivity-to-external-data.md) dans le guide des opérations de l’appliance.  
  
## <a name="ConnectingToIndividualNodes"></a>Connexion à des nœuds d’appliance  
Chacun des nœuds de l’appliance est accessible directement uniquement dans des scénarios d’utilisation spécifiques et par des types d’utilisateurs spécifiques. Le tableau suivant répertorie chaque nœud d’appliance et les scénarios dans lesquels les utilisateurs se connectent directement à ce nœud.  
  
<!-- MISSING LINKS For information on the purpose of each node, see [Understanding SQL Server PDW &#40;SQL Server PDW&#41;](../sqlpdw/understanding-sql-server-pdw-sql-server-pdw.md).  -->  

> [!WARNING]  
> La modification des paramètres d’une base de données ou d’une table sur des nœuds de contrôle ou de calcul sans consentement explicite de l’équipe de produit ou de l’équipe de support client APS risque de rendre votre appliance APS non prise en charge.
  
|||  
|-|-|  
|**Information**|**Scénarios d’accès**|  
|Nœud de contrôle|Utilisez un navigateur Web pour accéder à la console d’administration, qui s’exécute sur le nœud de contrôle. Pour plus d’informations, consultez [surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Toutes les applications et tous les outils clients se connectent au nœud de contrôle, que la connexion utilise Ethernet ou InfiniBand.<br /><br />Pour configurer une connexion Ethernet au nœud de contrôle, utilisez l’adresse IP de cluster du nœud de contrôle et le port **17001**. Par exemple, « 192.168.0.1, 17001 ».<br /><br />Pour configurer une connexion InfiniBand au nœud de contrôle, utilisez <strong> *appliance_domain*-SQLCTL01</strong> et le port **17001**. À l’aide de <strong> *appliance_domain*-SQLCTL01</strong>, le serveur DNS de l’appliance connecte votre serveur au réseau InfiniBand actif. Pour configurer votre serveur non-appareil pour l’utiliser, consultez [configurer des cartes réseau InfiniBand](configure-infiniband-network-adapters.md).<br /><br />L’administrateur de l’appareil se connecte au nœud de contrôle pour effectuer des opérations de gestion. Par exemple, l’administrateur de l’appliance effectue les opérations suivantes à partir du nœud de contrôle :<br /><br />Configurez Analytics Platform System avec l’outil de configuration **dwconfig. exe** .|  
|Nœud de calcul|Les connexions de nœud de calcul sont dirigées par le nœud de contrôle. Les adresses IP des nœuds de calcul ne sont jamais entrées en tant que paramètres dans les commandes d’application.<br /><br />Pour le chargement, la sauvegarde, la copie de table distante et Hadoop, SQL Server PDW envoie ou reçoit des données directement en parallèle entre les nœuds de calcul et les nœuds ou serveurs non-appliance. Ces applications se connectent avec SQL Server PDW en se connectant au nœud de contrôle, puis le nœud de contrôle dirige SQL Server PDW pour établir la communication entre les nœuds de calcul et le serveur non-appareil.<br /><br />Par exemple, ces opérations de transfert de données se produisent en parallèle avec des connexions directes aux nœuds de calcul :<br /><br />Chargement à partir du serveur de chargement vers SQL Server PDW.<br /><br />Sauvegarde d’une base de données de SQL Server PDW sur le serveur de sauvegarde.<br /><br />Restauration d’une base de données à partir du serveur de sauvegarde vers SQL Server PDW.<br /><br />Interrogation des données Hadoop à partir de SQL Server PDW.<br /><br />Exportation de données à partir d’SQL Server PDW vers une table Hadoop externe.<br /><br />Copie d’une table SQL Server PDW dans une base de données SMP SQL Server distante.|  
  
## <a name="connecting-to-the-ethernet-and-infiniband-networks"></a>Connexion aux réseaux Ethernet et InfiniBand  
Les serveurs distants peuvent se connecter via le réseau de l’appliance InfiniBand ou via le réseau Ethernet. Pour des raisons de performances, le chargement des serveurs, des serveurs de sauvegarde et des serveurs recevant des données via la **commande créer une table DIStante en tant qu’instructions SELECT** , transfère généralement les données via le réseau de l’appliance InfiniBand.  
  
Vous pouvez configurer des serveurs non-Appliance pour qu’ils appartiennent à votre propre domaine ou groupe de travail de client, puis utiliser votre propre réseau client pour vous connecter à ces serveurs et y transférer des données. En outre, les serveurs non-Appliance connectés à l’appliance InfiniBand ont la possibilité de transférer des données entre eux via le réseau de l’appliance InfiniBand. Soyez prudent avec cela, car cela peut ralentir les performances de SQL Server PDW.  
  
Par exemple, cette instruction ajoute des informations d’identification réseau pour effectuer des sauvegardes via InfiniBand vers un serveur de sauvegarde qui a une adresse IP InfiniBand 192.168.0.1. Le domaine de l’appliance est *mypdw*et l’instruction est exécutée à partir du serveur de sauvegarde. Avant d’exécuter cette instruction, vous devez remplir vos propres paramètres.  
  
```  
sqlcmd -S "mypdw-sqlctl01,17001" -U sa -P password -I -Q "exec sp_pdw_add_network_credentials '192.168.0.1', 'mypdw\Administrator', 'password'"  
```  
  
Par exemple, une commande de chargement démarre avec les éléments suivants :  
  
```  
dwloader -S mypdw-SQLCTL01  
```  
  
<!-- MISSING LINKS ## See Also  
[Configure an External Windows System To Receive Remote Table Copies Using InfiniBand &#40;SQL Server PDW&#41;](../sqlpdw/configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
