---
title: Introduction au Cloud hybride SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 6dc42752-1fcd-4ab9-8194-c3001ea342e7
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 026ed516989bde6f2c0b305d6af159f13a82f156
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358450"
---
# <a name="introduction-to-sql-server-2014-hybrid-cloud"></a>Introduction au cloud hybride SQL Server 2014
 La plupart des applications sont confrontées à des défis, tels qu'assurer une efficacité maximale ou une valeur commerciale, ou bien gérer des configurations matérielles complexes ou des pics importants à la demande, tout en respectant les règlements du secteur et de l'entreprise. Compte tenu de tous ces facteurs, la création d'une technologie de niveau enterprise est une tâche complexe. La stratégie de cloud hybride Microsoft prend en charge les environnements de cloud computing traditionnels, privés, publics et hybrides pour surmonter ces difficultés. 
 
 Si votre entreprise requiert une infrastructure informatique flexible capable d’évoluer à la demande, vous pouvez créer un cloud privé dans votre centre de données ou un cloud public dans les centres de données global Azure. Avec l'extension de votre centre de données au cloud public, vous créez un modèle de cloud hybride. 
 
 Cette rubrique présente les fonctionnalités de SQL Server 2014 qui prennent en charge les scénarios de cloud hybrides. Pour des informations détaillées sur la stratégie de cloud hybride de Microsoft et SQL Server, consultez le site Web [Informatique hybride SQL Server](https://www.microsoft.com/sqlserver/solutions-technologies/hybrid-It.aspx) . 
 
## <a name="sql-server-azure-and-hybrid-cloud"></a>SQL Server, Azure et Cloud hybride 
 Avec les technologies Microsoft, vous pouvez exécuter le code localement et dans le cloud, exécuter des applications dans le cloud à l'aide de données locales, ou bien en utilisant plus d'un centre de données. Par conséquent, vous pouvez migrer vos applications dans le cloud à votre rythme en conservant la valeur des investissements informatique existants. 
 
 Dans cet article, nous allons nous concentrer sur les scénarios de cloud hybride qui s’étendent à partir de la version locale SQL Server aux offres de cloud public Azure : [SQL Server dans Azure Virtual Machines](https://msdn.microsoft.com/library/azure/jj823132.aspx) et [stockage Azure](http://www.azure.com/documentation/services/storage/). Plus précisément, nous aborderons les scénarios suivants : 
 
-  [Sauvegarde et restauration de bases de données depuis/vers stockage Azure](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#backup) 
 
-  [Gérer les réplicas de base de données sur des Machines virtuelles](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#replica) 
 
-  [Store les fichiers de données SQL Server dans le stockage Azure](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#store) 
 
-  [Migrer des bases de données SQL Server existantes pour les Machines virtuelles](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#migrate) 
 
### <a name="hybrid-cloud-scenarios-for-sql-server-and-microsoft-azure"></a>Scénarios de Cloud hybride pour SQL Server et Microsoft Azure 
 
#### <a name="backup"></a> Sauvegarde et restauration de bases de données depuis/vers stockage Azure 
 Les deux tâches d'administration fondamentales sont la sauvegarde et la restauration de bases de données. Avec SQL Server et Azure, vous pouvez en toute sécurité sauvegarder vos bases de données dans le cloud. 
 
 Les principaux avantages d’utiliser les fonctionnalités de sauvegarde et de restauration de SQL Server avec le stockage Azure comme destination de sauvegarde sont : 
 
-  un stockage illimité à moindre coût ; 
 
-  un stockage hautement disponible (géographiquement répliqué pour éviter toute perte de données) ; 
 
-  un stockage hors site, pouvant prendre en charge des spécifications de récupération d'urgence et de conformité ; 
 
-  un processus distant simplifié de sauvegarde et de restauration. 
 
 La liste ci-dessous répertorie les fonctions de sauvegarde et de restauration de SQL Server pour les scénarios dans le cloud et sur site : 
 
-  Le [SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md) fonctionnalité vous permet d’effectuer une sauvegarde vers le stockage Azure en spécifiant une URL comme destination de sauvegarde. Avec cette fonctionnalité, vous effectuez une sauvegarde manuelle ou vous configurez votre propre stratégie de sauvegarde comme vous le feriez pour un stockage local ou d'autres options hors site. 
 
-  Le [chiffrement de sauvegarde](../relational-databases/backup-restore/backup-encryption.md) fonctionnalité vous permet de chiffrer les données lors de la création d’une sauvegarde pour vos destinations de stockage : en local et stockage Azure. 
 
-  Le [la Compression de sauvegarde (SQL Server)](../relational-databases/backup-restore/backup-compression-sql-server.md) fonctionnalité vous permet de créer une sauvegarde, ce qui est inférieure à une sauvegarde non compressée des mêmes données. La compression d'une sauvegarde nécessite moins d'E/S de périphérique et accélère généralement la sauvegarde de façon notable. Cela est très avantageux lorsque vous stockez des fichiers de sauvegarde dans le stockage Azure. 
 
-  Le [SQL Server Managed Backup to Azure](https://msdn.microsoft.com/library/dn606152(v=sql.120).aspx) fonctionnalité vous permet de sauvegarder automatiquement bases de données SQL Server à [stockage Azure](http://www.azure.com/documentation/services/storage/). Grâce à elle, vous configurez SQL Server pour qu'il gère la stratégie de sauvegarde et planifie les sauvegardes d'une seule ou de plusieurs bases de données, ou bien vous définissez les valeurs par défaut au niveau de l'instance. 
 
-  Le [SQL Server Backup to Azure Tool](https://www.microsoft.com/download/details.aspx?id=40740) permet le stockage Blob Azure et chiffre et compresse les sauvegardes SQL Server stockées localement ou dans le cloud. Cet outil active une seule stratégie de sauvegarde dans le cloud pour différentes versions de SQL Server, telles que SQL Server 2005, 2008, 2008 R2, et 2014. 
 
#### <a name="replica"></a> Gérer les réplicas de base de données sur des Machines virtuelles 
 Disposer d’une solution de récupération d’urgence stable pour vos bases de données est essentielle pour le succès de votre entreprise. La plupart des clients doivent configurer un site de récupération d'urgence et acheter du matériel supplémentaire pour les réplicas de base de données. Avec SQL Server et Azure, vous pouvez conserver un ou plusieurs réplicas de vos bases de données dans le cloud. 
 
 Les principaux avantages de la gestion des réplicas secondaires dans Azure sont : 
 
-  une solution de récupération d'urgence à moindre coût ; 
 
-  un basculement d'application transparent ; 
 
-  des réplicas disponibles pour décharger les charges de travail de lecture et les sauvegardes. 
 
 Vous pouvez gérer les réplicas secondaires dans Azure à l’aide des techniques suivantes : 
 
-  Le [Assistant Ajouter un réplica Azure](https://msdn.microsoft.com/library/dn463980\(v=sql.120\).aspx) vous permet de déployer un ou plusieurs réplicas de vos bases de données à une machine virtuelle dans Azure pour la récupération d’urgence. 
 
-  Groupes de disponibilité AlwaysOn, mise en miroir de base de données et l’envoi de journaux sont les technologies les plus courantes que vous pouvez utiliser pour aborder la haute disponibilité de votre application et de récupération d’urgence. Pour plus d’informations, consultez [haute disponibilité et récupération d’urgence pour SQL Server dans les Machines virtuelles](https://msdn.microsoft.com/library/azure/jj870962.aspx). 
 
#### <a name="store"></a> Store les fichiers de données SQL Server dans le stockage Azure 
 Stockage des fichiers de données SQL Server en local dans le stockage Azure fournit un stockage hors site flexible, fiable et illimité pour vos bases de données. À compter de SQL Server 2014, vous pouvez utiliser [fichiers de données SQL Server dans Azure de Miceosoft](https://docs.microsoft.com/sql/relational-databases/databases/sql-server-data-files-in-microsoft-azure) pour stocker les fichiers de base de données SQL Server dans le stockage Azure. Avec cette fonctionnalité, vous pouvez déplacer des données et fichiers journaux à partir de la base de données locale dans le stockage Azure, tout en conservant le nœud de calcul de SQL Server s’exécutant en local. Cette fonctionnalité vous permet d’avoir capacité de stockage illimitée dans le stockage Azure. 
 
 Les principaux avantages du stockage des fichiers de données SQL Server le stockage Azure sont : 
 
-  Stockage à faible coût illimité dans le stockage Azure 
 
-  un stockage mieux adapté pour décharger les charges de travail de lecture d'historique dans le cloud afin de prendre en charge des applications de création de rapports localement ; 
 
-  faciliter la récupération d'urgence en séparant l'instance de calcul (instance de SQL Server) et les données (fichiers de données SQL Server). Cela vous permet facilement attacher la base de données vers une autre instance de SQL Server dans un environnement local ou dans une machine virtuelle Azure en cas de sinistre. 
 
#### <a name="migrate"></a> Migrer des bases de données SQL Server existantes pour les Machines virtuelles 
 Le cloud computing offre un certain nombre d'avantages clés aux entreprises, notamment des ressources virtualisées illimitées et payables à l'utilisation. Vous exploitez ainsi des centres de données disponibles dans le cloud public au lieu de créer et gérer vos propres centres de données, ce qui réduit les coûts informatiques et les achats de matériel. 
 
 Avec [SQL Server dans Azure Virtual Machines](https://msdn.microsoft.com/library/azure/jj823132.aspx), vous pouvez déplacer les applications locales existantes vers Azure avec peu ou aucun code ne change. Les administrateurs et les développeurs utilisent toujours les mêmes outils de développement et d'administration disponibles localement. 
 
 Déplacement d’une base de données à partir de la version locale SQL Server à SQL Server s’exécutant dans une Machine virtuelle Azure généralement prend l’une de ces chemins d’accès : 
 
-  **Déplacement de la base de données uniquement :** Il existe plusieurs outils et techniques déplacer des bases de données locales existantes vers SQL Server dans les Machines virtuelles Azure. Pour des instructions et recommandations sur la migration vers SQL Server dans les Machines virtuelles Azure, consultez [se préparer à migrer vers SQL Server dans Azure Virtual Machines](https://msdn.microsoft.com/library/dn133142.aspx) et également [migration vers SQL Server dans une Machine virtuelle Azure ](https://msdn.microsoft.com/library/jj156165.aspx). 
 
   En outre, en commençant par SQL Server 2014, un nouvel Assistant [déployer une base de données SQL Server à une Machine virtuelle de Microsoft Azure](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md) est disponible pour vous permettre de déployer la base de données vers une autre instance de SQL Server en cours d’exécution dans une Machine virtuelle Azure. 
 
-  **Déplacement de la machine virtuelle complète :** Vous pouvez apporter vos propres machines virtuelles de SQL Server dans Azure, ou créez-en un à l’aide de l’image de plateforme. Ensuite, vous pouvez télécharger et attacher un disque de données qui contient déjà des données à la machine virtuelle, ou attacher un disque vide à la machine. Avoir une instance de données SQL Server sur des Machines virtuelles Azure avec des disques de données attachés fournit un stockage persistant supplémentaire pour vos fichiers de données et les données d’application. Pour obtenir des informations complètes et des procédures, consultez [déploiement de SQL Server dans les Machines virtuelles](https://msdn.microsoft.com/library/dn133141.aspx). 
 
 Si vous envisagez de déplacer les couches application (par exemple, la couche de présentation, le niveau métier et le niveau de base de données) aux Machines virtuelles Azure, nous vous recommandons de consulter les recommandations de le [modèles d’Application et de développement Stratégies pour SQL Server dans Azure Virtual Machines](https://msdn.microsoft.com/library/dn574746.aspx) article. L’objectif de cet article est de fournir aux architectes de solutions et aux développeurs une base pour l’architecture de la bonne application et la conception, qu’ils peuvent appliquer lors de la migration des applications existantes vers Azure, ainsi que développer de nouvelles applications dans Azure. Pour chaque modèle d'application, l'article décrit un scénario local, sa solution dans le cloud respective, et les recommandations techniques connexes. En outre, l’article aborde les stratégies de développement propres à Azure afin que vous pouvez concevoir correctement vos applications. 
 
## <a name="see-also"></a>Voir aussi 
 [Guide du produit SQL Server 2014 CTP2](https://www.microsoft.com/download/details.aspx?id=39269)  
 [SQL Server 2014](https://www.microsoft.com/sqlserver/sql-server-2014.aspx)  
 [Série de blogs Cloud de Microsoft SQL Server hybride](https://blogs.msdn.com/b/azure/archive/2013/10/16/microsoft-sql-server-hybrid-cloud-blog-series.aspx)  
 [Migration d’Applications centrées sur les données vers Azure](https://msdn.microsoft.com/library/jj156154.aspx) 
 
 
