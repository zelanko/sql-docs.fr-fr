---
title: "Configuration de SQL Server (Services R) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4b08969f-b90b-46b3-98e7-0bf7734833fc
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Configuration de SQL Server (Services R)
Les informations contenues dans cette section fournissent des indications générales sur la configuration matérielle et réseau de l’ordinateur qui est utilisé pour l’hôte [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Il doit être envisagée en plus de l’onglet Général [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] informations fournies dans le réglage des performances du [Centre de performances pour le moteur de base de données SQL Server et la base de données SQL Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## Processeur

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] peut effectuer des tâches en parallèle à l’aide du nombre de cœurs disponibles sur l’ordinateur ; davantage de cœurs disponibles, meilleures sont les performances. Étant donné que [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] est normalement utilisé par plusieurs utilisateurs simultanément, l’administrateur doit déterminer le nombre idéal de cœurs qui sont nécessaires pour prendre en charge les calculs de la charge de travail maximale. Bien que le nombre de cœurs sera d’aucune utilité pour les opérations e/s, le processeur de manière intensive algorithmes bénéficieront des processeurs plus rapides avec un nombre de cœurs.

## Mémoire

La quantité de mémoire disponible sur l’ordinateur peut avoir un impact important sur les performances des algorithmes d’analyse avancés. Mémoire insuffisante peut affecter le degré de parallélisme lors de l’utilisation du contexte de calcul SQL. Il peut également affecter la taille de segment (lignes par opération de lecture) qui peut être traitée et le nombre de sessions simultanées pouvant être pris en charge.

Un minimum de 32 Go est fortement recommandé. Si vous avez plus de 32 Go de disponible, vous pouvez configurer la source de données SQL pour utiliser plus de lignes dans chaque opération de lecture pour améliorer les performances.

## Options d’alimentation

Sur le système d’exploitation Windows, le __hautes performances__ d’alimentation doit être utilisée. À l’aide d’un paramètre d’alimentation différents entraîne des performances réduites ou incohérentes lors de l’utilisation [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

## E/s disque

Tâches d’apprentissage et la prédiction à l’aide [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sont par nature des e/s liée et dépendent de la vitesse de la base de données stockées sur les disques. Les disques plus rapides, tels que les lecteurs SSD (SSD) peuvent aider. 

E/s disque est également affecté par d’autres applications d’accès au disque : par exemple, lire des opérations sur une base de données par d’autres clients. Performances d’e/s de disque peut également être affecté par les paramètres du système de fichiers en cours d’utilisation, telles que la taille de bloc utilisée par le système de fichiers. Si plusieurs lecteurs sont disponibles, stockez les bases de données sur un lecteur différent de celui [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ainsi que les demandes de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ne sont pas en appuyant sur le même disque que les demandes pour les données stockées dans la base de données.

E/s disque peut affecter considérablement les performances lors de l’exécution des fonctions analytiques RevoScaleR qui utilisent plusieurs itérations pendant la formation. Par exemple, `rxLogit`, `rxDTree`, `rxDForest` et `rxBTrees` tous utiliser plusieurs itérations. Lorsque la source de données est [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], ces algorithmes utilisant des fichiers temporaires qui sont optimisés pour capturer les données. Ces fichiers sont automatiquement nettoyés une fois la session terminée. Avoir un disque hautes performances pour les opérations de lecture/écriture peut améliorer considérablement le temps écoulé global pour ces algorithmes.

> [!NOTE]
> [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] nécessite la prise en charge de nom de fichier au format 8.3 sur les systèmes d’exploitation Windows. Vous pouvez utiliser fsutil.exe pour déterminer si un lecteur prend en charge les noms de 8.3 fichiers ou activer la prise en charge s’il n’existe pas. Pour plus d’informations sur l’utilisation de fsutil.exe avec des noms de 8.3 fichiers, consultez [Fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

### Compression de table

Pouvez souvent améliorer les performances d’e/s à l’aide de la compression ou les index columstore. En règle générale, les données sont souvent répétées dans plusieurs colonnes dans une table, afin d’utiliser un index columnstore exploite ces répétitions lors de la compression des données.

Un index columnstore peut ne pas être aussi efficace s’il existe un grand nombre d’insertions dans la table, mais est un bon choix si les données sont statiques ou ne modifie que rarement. Si une banque de colonnes n’est pas appropriée, l’activation de la compression sur une table principale de lignes peut servir à améliorer d’e/s.

Pour plus d’informations, consultez les documents suivants :

* [Compression de données](../../relational-databases/data-compression/data-compression.md)

* [Activer la compression sur une table ou un index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

* [Guide des index columnstore](Columnstore%20Indexes%20Guide.md)

## Fichier d’échange

Le système d’exploitation Windows utilise un fichier de pagination pour gérer les vidages sur incident et pour le stockage des pages de mémoire virtuelle. Si vous remarquez une pagination excessive, envisagez d’augmenter la mémoire physique sur l’ordinateur. Bien qu’ayant plus de mémoire physique n’élimine pas la pagination, il réduit la nécessité pour la pagination.

La vitesse du disque stockées dans le fichier d’échange peut également affecter les performances. Stocker le fichier d’échange sur un disque SSD, ou à l’aide de plusieurs fichiers d’échange entre plusieurs SSDs, peut améliorer les performances.

Consultez [comment déterminer la taille de page appropriée pour les versions 64 bits de Windows](https://support.microsoft.com/en-us/kb/2860880) Pour plus d’informations sur le dimensionnement de la page du fichier.

## Gestion des ressources

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] prend en charge la gestion des ressources permettant de contrôler diverses ressources utilisées par [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Par exemple, la valeur par défaut pour la consommation de mémoire par R est limitée à 20 % de la mémoire totale disponible pour [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Cela est fait pour vous assurer que [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] des flux de travail n’est pas gravement affectés par les travaux de longue durée R. Toutefois, ces limites peuvent être modifiés par l’administrateur de base de données. 

Les ressources limitées sont __MAX_CPU_PERCENT__, __MAX_MEMORY_PERCENT__, et __MAX_PROCESSES__. Pour afficher les paramètres actuels, utilisez cette [!INCLUDE[tsql_md](../../includes/tsql-md.md)] instruction :

```T-SQL
SELECT * FROM sys.resource_governor_external_resource_pools
``` 

Si [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] est principalement utilisé pour les Services de R, il peut être utile d’augmenter MAX_CPU_PERCENT à 40 % ou 60 %. S’il n’y a plusieurs sessions de R en utilisant le même [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] augmente en même temps, les trois. Pour modifier les valeurs de ressource, utilisez [!INCLUDE[tsql_md](../../includes/tsql-md.md)] instructions. 

Cet exemple définit l’utilisation de la mémoire à 40 % :

```T-SQL
ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)
```
L’exemple suivant définit les trois valeurs configurables :
```T-SQL
ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`
``` 

> [!NOTE]
> Pour apporter des modifications à ces paramètres prennent effet immédiatement, exécutez l’instruction `ALTER RESOURCE GOVERNOR RECONFIGURE` après avoir modifié une mémoire, processeur ou le paramètre du processus maximale. 

## Voir aussi
[Resource Governor](../../relational-databases/resource-governor/resource-governor.md)

[CRÉER LE POOL DE RESSOURCES EXTERNES](../../t-sql/statements/create-external-resource-pool-transact-sql.md)

 [Guide de réglage de performances SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
 
 [Étude de cas de performances](../../advanced-analytics/r-services/performance-case-study-r-services.md)
 
 [R et optimisation des données](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md)