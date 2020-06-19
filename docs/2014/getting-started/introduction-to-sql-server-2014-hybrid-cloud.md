---
title: Présentation de SQL Server Cloud hybride 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6dc42752-1fcd-4ab9-8194-c3001ea342e7
author: rothja
ms.author: jroth
ms.openlocfilehash: 93282199db986ab8bcf18b05f9ae8b61a5a45b9a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84926740"
---
# <a name="introduction-to-sql-server-2014-hybrid-cloud"></a>Introduction au cloud hybride SQL Server 2014
 La plupart des applications sont confrontées à des défis, tels qu'assurer une efficacité maximale ou une valeur commerciale, ou bien gérer des configurations matérielles complexes ou des pics importants à la demande, tout en respectant les règlements du secteur et de l'entreprise. Compte tenu de tous ces facteurs, la création d'une technologie de niveau enterprise est une tâche complexe. La stratégie de cloud hybride Microsoft prend en charge les environnements de cloud computing traditionnels, privés, publics et hybrides pour surmonter ces difficultés. 
 
 Lorsque votre entreprise a besoin d’une infrastructure informatique flexible qui peut évoluer à la demande, vous pouvez créer un Cloud privé dans votre centre de données ou un cloud public dans les centres de données globaux Azure. Avec l'extension de votre centre de données au cloud public, vous créez un modèle de cloud hybride. 
 
 Cette rubrique présente les fonctionnalités de SQL Server 2014 qui prennent en charge les scénarios de cloud hybrides. Pour des informations détaillées sur la stratégie de cloud hybride de Microsoft et SQL Server, consultez le site Web [Informatique hybride SQL Server](https://www.microsoft.com/sqlserver/solutions-technologies/hybrid-It.aspx) . 
 
## <a name="sql-server-azure-and-hybrid-cloud"></a>SQL Server, Azure et le Cloud hybride 
 Avec les technologies Microsoft, vous pouvez exécuter le code localement et dans le cloud, exécuter des applications dans le cloud à l'aide de données locales, ou bien en utilisant plus d'un centre de données. Par conséquent, vous pouvez migrer vos applications dans le cloud à votre rythme en conservant la valeur des investissements informatique existants. 
 
 Dans cet article, nous nous concentrerons sur les scénarios de Cloud hybrides qui s’étendent du SQL Server local aux offres de cloud public Azure : [SQL Server dans les machines virtuelles Azure](https://msdn.microsoft.com/library/azure/jj823132.aspx) et le [stockage Azure](https://www.azure.com/documentation/services/storage/). Plus précisément, nous aborderons les scénarios suivants : 
 
-  [Sauvegarder et restaurer des bases de données vers/à partir de stockage Azure](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#backup) 
 
-  [Conserver les réplicas de base de données sur les machines virtuelles Azure](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#replica) 
 
-  [Stocker des fichiers de données SQL Servers dans le stockage Azure](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#store) 
 
-  [Migrer des bases de données SQL Server existantes vers des machines virtuelles Azure](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#migrate) 
 
### <a name="hybrid-cloud-scenarios-for-sql-server-and-microsoft-azure"></a>Scénarios de Cloud hybride pour SQL Server et Microsoft Azure 
 
#### <a name="backup-and-restore-databases-tofrom-azure-storage"></a><a name="backup"></a>Sauvegarder et restaurer des bases de données vers/à partir de stockage Azure 
 Les deux tâches d'administration fondamentales sont la sauvegarde et la restauration de bases de données. Avec SQL Server et Azure, vous pouvez sauvegarder vos bases de données dans le Cloud en toute sécurité. 
 
 Les principaux avantages de l’utilisation des fonctionnalités de sauvegarde et de restauration de SQL Server avec le stockage Azure en tant que destination de sauvegarde sont les suivants : 
 
-  un stockage illimité à moindre coût ; 
 
-  un stockage hautement disponible (géographiquement répliqué pour éviter toute perte de données) ; 
 
-  un stockage hors site, pouvant prendre en charge des spécifications de récupération d'urgence et de conformité ; 
 
-  un processus distant simplifié de sauvegarde et de restauration. 
 
 La liste ci-dessous répertorie les fonctions de sauvegarde et de restauration de SQL Server pour les scénarios dans le cloud et sur site : 
 
-  La fonctionnalité [SQL Server sauvegarde vers une URL](../relational-databases/backup-restore/sql-server-backup-to-url.md) vous permet de sauvegarder dans le stockage Azure en spécifiant l’URL comme destination de sauvegarde. Avec cette fonctionnalité, vous effectuez une sauvegarde manuelle ou vous configurez votre propre stratégie de sauvegarde comme vous le feriez pour un stockage local ou d'autres options hors site. 
 
-  La fonctionnalité de [chiffrement de sauvegarde](../relational-databases/backup-restore/backup-encryption.md) vous permet de chiffrer les données lors de la création d’une sauvegarde pour vos destinations de stockage : stockage local et stockage Azure. 
 
-  La fonctionnalité de compression de la [sauvegarde (SQL Server)](../relational-databases/backup-restore/backup-compression-sql-server.md) vous permet de créer une sauvegarde, qui est plus petite qu’une sauvegarde non compressée des mêmes données. La compression d'une sauvegarde nécessite moins d'E/S de périphérique et accélère généralement la sauvegarde de façon notable. Cela peut offrir de nombreux avantages lors du stockage des fichiers de sauvegarde dans le stockage Azure. 
 
-  La fonctionnalité de [gestion des sauvegardes SQL Server sur Azure](https://msdn.microsoft.com/library/dn606152(v=sql.120).aspx) vous permet de sauvegarder automatiquement les bases de données SQL Server dans le [stockage Azure](https://www.azure.com/documentation/services/storage/). Grâce à elle, vous configurez SQL Server pour qu'il gère la stratégie de sauvegarde et planifie les sauvegardes d'une seule ou de plusieurs bases de données, ou bien vous définissez les valeurs par défaut au niveau de l'instance. 
 
-  L' [outil de sauvegarde de SQL Server sur Azure](https://www.microsoft.com/download/details.aspx?id=40740) permet de sauvegarder dans le stockage d’objets BLOB Azure et de chiffrer et de compresser SQL Server sauvegardes stockées localement ou dans le Cloud. Cet outil active une seule stratégie de sauvegarde dans le cloud pour différentes versions de SQL Server, telles que SQL Server 2005, 2008, 2008 R2, et 2014. 
 
#### <a name="maintain-database-replicas-on-azure-virtual-machines"></a><a name="replica"></a>Conserver les réplicas de base de données sur les machines virtuelles Azure 
 Une solution de récupération d’urgence stable pour vos bases de données est essentielle pour la réussite de votre entreprise. La plupart des clients doivent configurer un site de récupération d'urgence et acheter du matériel supplémentaire pour les réplicas de base de données. Avec SQL Server et Azure, vous pouvez gérer un ou plusieurs réplicas de vos bases de données dans le Cloud. 
 
 Les principaux avantages de la gestion des réplicas secondaires dans Azure sont les suivants : 
 
-  une solution de récupération d'urgence à moindre coût ; 
 
-  un basculement d'application transparent ; 
 
-  des réplicas disponibles pour décharger les charges de travail de lecture et les sauvegardes. 
 
 Vous pouvez gérer les réplicas secondaires dans Azure à l’aide de l’une des techniques suivantes : 
 
-  L' [Assistant Ajout d’un réplica Azure](https://msdn.microsoft.com/library/dn463980\(v=sql.120\).aspx) vous permet de déployer un ou plusieurs réplicas de vos bases de données sur une machine virtuelle dans Azure pour la récupération d’urgence. 
 
-  Groupes de disponibilité AlwaysOn, la mise en miroir de bases de données et la copie des journaux de session sont les technologies les plus courantes que vous pouvez utiliser pour répondre aux besoins de haute disponibilité et de récupération d’urgence de votre application. Pour plus d’informations, consultez [haute disponibilité et récupération d’urgence pour SQL Server dans machines virtuelles Azure](https://msdn.microsoft.com/library/azure/jj870962.aspx). 
 
#### <a name="store-sql-server-data-files-in-azure-storage"></a><a name="store"></a>Stocker des fichiers de données SQL Servers dans le stockage Azure 
 Le stockage des fichiers de données SQL Server locaux dans le stockage Azure fournit un stockage hors site flexible, fiable et illimité pour vos bases de données. À compter de SQL Server 2014, vous pouvez utiliser des [fichiers de données SQL Server dans Miceosoft Azure](https://docs.microsoft.com/sql/relational-databases/databases/sql-server-data-files-in-microsoft-azure) pour stocker des fichiers de base de données SQL Server dans le stockage Azure. Avec cette fonctionnalité, vous pouvez déplacer les fichiers de données et les fichiers journaux de la base de données locale vers le stockage Azure, tout en conservant le nœud de calcul de SQL Server s’exécutant en local. Cette fonctionnalité vous permet de disposer d’une capacité de stockage illimitée dans le stockage Azure. 
 
 Les principaux avantages du stockage des fichiers de données SQL Server stockage Azure sont les suivants : 
 
-  Stockage à faible coût illimité dans le stockage Azure 
 
-  un stockage mieux adapté pour décharger les charges de travail de lecture d'historique dans le cloud afin de prendre en charge des applications de création de rapports localement ; 
 
-  faciliter la récupération d'urgence en séparant l'instance de calcul (instance de SQL Server) et les données (fichiers de données SQL Server). Cela vous permet d’attacher facilement la base de données à une autre instance de SQL Server dans un environnement local ou dans une machine virtuelle Azure en cas de sinistre. 
 
#### <a name="migrate-existing-sql-server-databases-to-azure-virtual-machines"></a><a name="migrate"></a>Migrer des bases de données SQL Server existantes vers des machines virtuelles Azure 
 Le cloud computing offre un certain nombre d'avantages clés aux entreprises, notamment des ressources virtualisées illimitées et payables à l'utilisation. Vous exploitez ainsi des centres de données disponibles dans le cloud public au lieu de créer et gérer vos propres centres de données, ce qui réduit les coûts informatiques et les achats de matériel. 
 
 Avec [SQL Server dans les machines virtuelles Azure](https://msdn.microsoft.com/library/azure/jj823132.aspx), vous pouvez déplacer les applications locales existantes vers Azure avec un minimum de modifications de code. Les administrateurs et les développeurs utilisent toujours les mêmes outils de développement et d'administration disponibles localement. 
 
 Le déplacement d’une base de données à partir d’un SQL Server local vers SQL Server exécuté sur une machine virtuelle Azure prend généralement l’un des chemins d’accès suivants : 
 
-  **Déplacement de la base de données uniquement :** Plusieurs outils et techniques sont disponibles pour déplacer des bases de données locales existantes vers des SQL Server dans des machines virtuelles Azure. Pour obtenir des instructions et des recommandations sur la migration vers SQL Server sur des machines virtuelles Azure, consultez se [préparer à migrer vers SQL Server sur des machines virtuelles Azure](https://msdn.microsoft.com/library/dn133142.aspx) et [migrer vers SQL Server sur une machine virtuelle Azure](https://msdn.microsoft.com/library/jj156165.aspx). 
 
   En outre, à compter de SQL Server 2014, un nouvel Assistant, [déployer une base de données SQL Server sur une machine virtuelle Microsoft Azure](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md) , vous permet de déployer la base de données sur une autre instance de SQL Server s’exécutant sur une machine virtuelle Azure. 
 
-  **Déplacement de la totalité de la machine virtuelle :** Vous pouvez placer vos propres machines virtuelles SQL Server sur Azure ou en créer une à l’aide de l’image de plateforme. Ensuite, vous pouvez télécharger et attacher un disque de données qui contient déjà des données à la machine virtuelle, ou attacher un disque vide à la machine. Le fait de disposer d’une instance de données SQL Server sur des machines virtuelles Azure avec des disques de données attachés fournit un autre stockage persistant pour vos fichiers de données et vos données d’application. Pour obtenir des informations complètes et des procédures, consultez [SQL Server le déploiement sur des machines virtuelles Azure](https://msdn.microsoft.com/library/dn133141.aspx). 
 
 Si vous envisagez de déplacer les couches application (telles que la couche présentation, le niveau entreprise et la couche base de données) vers des machines virtuelles Azure, nous vous recommandons de consulter les recommandations fournies dans l’article [modèles d’application et stratégies de développement pour SQL Server dans machines virtuelles Azure](https://msdn.microsoft.com/library/dn574746.aspx) . Cet article vise à fournir aux architectes de solutions et aux développeurs une base pour une architecture et une conception de qualité, qu’ils peuvent appliquer lors de la migration d’applications existantes vers Azure ainsi que dans le cadre du développement de nouvelles applications dans Azure. Pour chaque modèle d'application, l'article décrit un scénario local, sa solution dans le cloud respective, et les recommandations techniques connexes. En outre, l’article aborde des stratégies de développement propres à Azure afin de vous permettre de concevoir correctement vos applications. 
 
## <a name="see-also"></a>Voir aussi 
 [Guide du produit SQL Server 2014 CTP2](https://www.microsoft.com/download/details.aspx?id=39269)  
 [SQL Server 2014](https://www.microsoft.com/sqlserver/sql-server-2014.aspx)  
 [Série de blogs cloud hybride de Microsoft SQL Server](https://azure.microsoft.com/blog/microsoft-sql-server-hybrid-cloud-blog-series/)  
 [Migration d'applications centrées sur les données vers Azure](https://azure.microsoft.com/blog/cloud-services-series-migrating-data-centric-applications-to-windows-azure/) 
 
