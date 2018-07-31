---
title: Mise à jour d’une application vers OLE DB Driver pour SQL Server à partir de MDAC | Microsoft Docs
description: Mise à jour d’une application vers OLE DB Driver pour SQL Server à partir de MDAC
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, vs. MDAC
- OLE DB Driver for SQL Server, vs. MDAC
- data access [OLE DB Driver for SQL Server], vs. MDAC
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 173b49bb4c63c124579153585f07993c9a5ba691
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106775"
---
# <a name="updating-an-application-to-ole-db-driver-for-sql-server-from-mdac"></a>Mise à jour d’une application vers OLE DB Driver pour SQL Server à partir de MDAC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il existe plusieurs différences entre OLE DB Driver pour SQL Server et MDAC (Microsoft Data Access Components). À compter de Windows Vista, MDAC prend le nom de « Windows DAC » (ou Windows Data Access Components). Même si ces deux solutions fournissent aux données natives un accès aux bases de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], OLE DB Driver pour SQL Server a été spécialement conçu pour exposer les nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], tout en restant compatible avec les versions antérieures.   

 En outre, bien que MDAC contienne des composants permettant d’utiliser OLE DB, ODBC et ActiveX Data Objects (ADO), OLE DB Driver pour SQL Server implémente uniquement OLE DB (bien qu’ADO permettre accéder aux fonctionnalités du pilote OLE DB pour SQL Server).  

 OLE DB Driver pour SQL Server et MDAC diffèrent dans les domaines suivants :  

-   Les utilisateurs qui utilisent ADO pour accéder à OLE DB Driver pour SQL Server peuvent trouver moins de fonctionnalités de filtrage qu’en le fournisseur SQL OLE DB.  

-   Si une application ADO utilise OLE DB Driver pour SQL Server et tente de mettre à jour une colonne calculée, une erreur sera signalée. Avec MDAC, la mise à jour était acceptée mais ignorée.  

-   OLE DB Driver pour SQL Server est un fichier de bibliothèque (DLL) unique de liens dynamiques autonome. Les interfaces exposées publiquement ont été limitées en nombre pour faciliter la distribution et limiter l'exposition de sécurité.  

-   Seules les interfaces OLE DB sont prises en charge.  

-   Le pilote OLE DB pour les noms de SQL Server sont différents des noms utilisés avec MDAC.  

-   Les fonctionnalités accessibles à l’utilisateur fournies par les composants MDAC sont disponibles lors de l’utilisation d’OLE DB Driver pour SQL Server. Cela comprend, entre autres, le regroupement de connexions, la prise en charge des objets ADO et la prise en charge du curseur client. Lorsqu’une de ces fonctionnalités sont utilisée, OLE DB Driver pour SQL Server fournit uniquement la connectivité de base de données. MDAC fournit des fonctionnalités telles que le suivi, des contrôles de gestion et des compteurs de performance.  

-   Les applications peuvent utiliser les services principaux OLE DB avec OLE DB Driver pour SQL Server, mais si elles utilisent le moteur de curseur OLE DB, elles doivent utiliser l’option de compatibilité du type de données pour éviter tout problème pouvant résulter du fait que le moteur de curseur n’a pas connaissance des nouveaux types de données [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  

-   OLE DB Driver pour SQL Server prend en charge l’accès à la précédente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bases de données.  

-   OLE DB Driver pour SQL Server ne contient pas d’intégration de XML. OLE DB Driver pour SQL Server prend en charge SELECT... POUR les requêtes de XML, mais ne prend pas en charge d’autres fonctionnalités XML. Toutefois, le pilote OLE DB pour SQL Server prend en charge la **xml** type de données introduits dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  

-   OLE DB Driver pour SQL Server prend en charge la configuration de bibliothèques réseau côté client à l’aide d’attributs de chaîne de connexion uniquement. Pour configurer une bibliothèque réseau de manière plus complète, vous devez utiliser le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  

-   Chaînes de connexion MDAC autorisent une valeur booléenne (**true**) pour le **Trusted_Connection** mot clé. Un pilote OLE DB pour la chaîne de connexion SQL Server doit utiliser **Oui** ou **aucun**.  

-   Des changements mineurs affectent les avertissements et les erreurs. Les avertissements et les erreurs retournées par le serveur conservent désormais la même gravité quand ils sont passés à OLE DB Driver pour SQL Server. Vous devez vous assurer d'avoir rigoureusement testé votre application si vous comptez sur l'interception d'avertissements et d'erreurs particuliers.  

-   OLE DB Driver pour SQL Server effectue une vérification des erreurs plus stricte que MDAC, ce qui signifie que certaines applications qui ne sont pas strictement conformes aux spécifications OLE DB peuvent se comporter différemment. Par exemple, contrairement au fournisseur OLE DB Driver pour SQL Server, le fournisseur SQLOLEDB n’appliquait pas la règle selon laquelle les noms de paramètre doivent commencer par « \@ »pour les paramètres de résultat.  

-   OLE DB Driver pour SQL Server se comporte différemment de MDAC en ce qui concerne les connexions ayant échoué. Par exemple, MDAC retourne des valeurs de propriété mises en cache pour une connexion qui a échoué, alors qu’OLE DB Driver pour SQL Server signale une erreur à l’application appelante.  

-   OLE DB Driver pour SQL Server ne génère pas d’événements Visual Studio Analyzer, mais il génère à la place des événements de suivi Windows.  

-   OLE DB Driver pour SQL Server ne peut pas être utilisé avec perfmon. Perfmon est un outil Windows qui peut être uniquement utilisé avec des noms de source de données (DSN) qui utilisent le pilote MDAC SQLODBC inclus avec Windows.  

-   Quand le pilote OLE DB pour SQL Server est connecté à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures, erreur de serveur 16947 est retournée en tant que SQL_ERROR. Cette erreur se produit lorsqu'une mise à jour ou une suppression positionnée ne parvient pas à mettre à jour ou à supprimer une ligne. Avec MDAC lors de la connexion à n'importe quelle version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'erreur de serveur 16947 est retournée en tant qu'avertissement (SQL_SUCCESS_WITH_INFO).  

-   OLE DB Driver pour SQL Server implémente l’interface **IDBDataSourceAdmin**, qui est une interface OLE DB facultative qui n’était pas précédemment implémentée, mais seule la méthode **CreateDataSource** de cette interface facultative est implémentée. [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  

-   Le fournisseur OLE DB Driver pour SQL Server retourne des synonymes dans les ensembles de lignes de schéma TABLES et TABLE_INFO, avec la valeur SYNONYM attribuée à TABLE_TYPE.  

-   Les valeurs de retour du type de données **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **xml**, **udt** ou de tout autre type d’objet volumineux ne peuvent pas être retournées aux versions de client antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Si vous souhaitez utiliser ces types comme valeurs de retour, vous devez utiliser le pilote OLE DB pour SQL Server.  

-   Contrairement à OLE DB Driver pour SQL Server, MDAC permet l’exécution des instructions suivantes au démarrage de transactions manuelles et implicites. Elles doivent être exécutées en mode de validation automatique.  

    -   Tous les opérations de texte intégral (DDL d'index et de catalogue)  

    -   Toutes les opérations de base de données (create database, alter database, drop database)  

    -   Reconfiguration  

    -   Arrêter  

    -   Kill  

    -   Backup  

-   Lorsque des applications MDAC se connectent à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les types de données introduits dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] apparaissent en tant que types de données compatibles avec [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], comme indiqué dans le tableau suivant.  

    |Type SQL Server 2005|Type SQL Server 2000|  
    |--------------------------|--------------------------|  
    |**varchar(max)**|**text**|  
    |**nvarchar(max)**|**ntext**|  
    |**varbinary(max)**|**image**|  
    |**udt**|**varbinary**|  
    |**xml**|**ntext**|  

     Ce mappage de type affecte les valeurs retournées pour les métadonnées de colonne. Par exemple, un **texte** colonne a une taille maximale de 2 147 483 647, mais le pilote OLE DB pour SQL Server indique la taille maximale de **varchar (max)** colonnes en tant que 2 147 483 647 ou -1, en fonction de la plateforme.  

-   Pour des raisons de compatibilité descendante, OLE DB Driver pour SQL Server autorise l’ambiguïté dans les chaînes de connexion (par exemple, certains mots clés peuvent être spécifiés plusieurs fois et des mots clés en conflit peuvent être autorisés avec la résolution basée sur la position ou la précédence). Les versions futures du pilote OLE DB pour SQL Server ne permettent pas d’ambiguïté dans les chaînes de connexion. Lors de la modification d’applications, il est conseillé d’utiliser OLE DB Driver pour SQL Server pour éliminer toute dépendance vis-à-vis de l’ambiguïté des chaînes de connexion.  

-   Si vous utilisez un appel OLE DB pour démarrer des transactions, il existe une différence de comportement entre OLE DB Driver pour SQL Server et MDAC : transactions commencent immédiatement avec OLE DB Driver pour SQL Server, mais les transactions commencent après la première base de données accéder à l’aide de MDAC. Cela peut affecter le comportement de procédures stockées et de lots, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nécessitant que @@TRANCOUNT soit le même entre le démarrage et la fin de l’exécution d’un lot ou d’une procédure stockée.  

-   Avec OLE DB Driver pour SQL Server, ITransactionLocal::BeginTransaction entraîne une transaction doit être démarré immédiatement. Avec MDAC, le démarrage de la transaction était différé jusqu’à ce que l’application exécute une instruction qui exigeait une transaction en mode de transaction implicite. Pour plus d’informations, consultez [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../../t-sql/statements/set-implicit-transactions-transact-sql.md).  


 Les deux OLE DB Driver pour SQL Server et MDAC prennent en charge l’isolation de transaction validée à l’aide de la version de ligne, mais uniquement pilote OLE DB SQL Server prend en charge la capture instantanée d’isolation des transactions de lecture. (En termes de programmation, l'isolation de la transaction de lecture validée à l'aide du contrôle de version de ligne est la même chose que la transaction de lecture validée.)  

## <a name="see-also"></a> Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
