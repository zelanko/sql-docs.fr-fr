---
title: Mise à jour d’une application vers OLE DB Driver pour SQL Server à partir de MDAC | Microsoft Docs
description: Mise à jour d’une application vers OLE DB Driver pour SQL Server à partir de MDAC
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, vs. MDAC
- OLE DB Driver for SQL Server, vs. MDAC
- data access [OLE DB Driver for SQL Server], vs. MDAC
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: pelopes
ms.openlocfilehash: ad36a17367b14a48810d83137b2887eaa75f6ef1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989262"
---
# <a name="updating-an-application-to-ole-db-driver-for-sql-server-from-mdac"></a>Mise à jour d’une application vers OLE DB Driver pour SQL Server à partir de MDAC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il existe plusieurs différences entre OLE DB Driver pour SQL Server et MDAC (Microsoft Data Access Components). À compter de Windows Vista, MDAC prend le nom de « Windows DAC » (ou Windows Data Access Components). Même si ces deux solutions fournissent aux données natives un accès aux bases de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], OLE DB Driver pour SQL Server a été spécialement conçu pour exposer les nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], tout en restant compatible avec les versions antérieures.   

 En outre, bien que MDAC contienne des composants pour l’utilisation de OLE DB, ODBC et ActiveX Data Objects (ADO), OLE DB Driver for SQL Server implémente uniquement OLE DB (même si ADO peut accéder aux fonctionnalités de OLE DB Driver pour SQL Server).  

 OLE DB pilote pour SQL Server et MDAC diffèrent dans les autres domaines suivants:  

-   Les utilisateurs qui utilisent ADO pour accéder au pilote OLE DB pour SQL Server peuvent trouver moins de fonctionnalités de filtrage que lorsqu’ils accèdent au fournisseur SQL OLE DB.  

-   Si une application ADO utilise OLE DB pilote pour SQL Server et tente de mettre à jour une colonne calculée, une erreur est signalée. Avec MDAC, la mise à jour était acceptée mais ignorée.  

-   OLE DB pilote pour SQL Server est un seul fichier de bibliothèque de liens dynamiques (DLL) autonome. Les interfaces exposées publiquement ont été limitées en nombre pour faciliter la distribution et limiter l'exposition de sécurité.  

-   Seules les interfaces OLE DB sont prises en charge.  

-   Le pilote OLE DB pour les noms de SQL Server est différent des noms utilisés avec MDAC.  

-   Les fonctionnalités accessibles à l’utilisateur fournies par les composants MDAC sont disponibles lors de l’utilisation d’OLE DB Driver pour SQL Server. Cela comprend, entre autres, le regroupement de connexions, la prise en charge des objets ADO et la prise en charge du curseur client. Quand l’une de ces fonctionnalités est utilisée, OLE DB pilote pour SQL Server fournit uniquement la connectivité de base de données. MDAC fournit des fonctionnalités telles que le suivi, des contrôles de gestion et des compteurs de performance.  

-   Les applications peuvent utiliser les services principaux OLE DB avec OLE DB Driver pour SQL Server, mais si elles utilisent le moteur de curseur OLE DB, elles doivent utiliser l’option de compatibilité du type de données pour éviter tout problème pouvant résulter du fait que le moteur de curseur n’a pas connaissance des nouveaux types de données [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  

-   OLE DB pilote pour SQL Server prend en charge l' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] accès aux bases de données précédentes.  

-   OLE DB pilote pour SQL Server ne contient pas d’intégration XML. OLE DB pilote pour SQL Server prend en charge SELECT... Les requêtes FOR XML, mais ne prennent pas en charge d’autres fonctionnalités XML. Toutefois, OLE DB pilote pour SQL Server prend en charge  le type de données **XML** [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]introduit dans.  

-   OLE DB Driver pour SQL Server prend en charge la configuration de bibliothèques réseau côté client à l’aide d’attributs de chaîne de connexion uniquement. Pour configurer une bibliothèque réseau de manière plus complète, vous devez utiliser le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  

-   Les chaînes de connexion MDAC autorisent une valeur booléenne (**true**) pour le mot clé **Trusted_Connection** . Un pilote de OLE DB pour SQL Server chaîne de connexion doit utiliser **Oui** ou **non**.  

-   Des changements mineurs affectent les avertissements et les erreurs. Les avertissements et les erreurs retournées par le serveur conservent désormais la même gravité quand ils sont passés à OLE DB Driver pour SQL Server. Vous devez vous assurer d'avoir rigoureusement testé votre application si vous comptez sur l'interception d'avertissements et d'erreurs particuliers.  

-   OLE DB Driver pour SQL Server effectue une vérification des erreurs plus stricte que MDAC, ce qui signifie que certaines applications qui ne sont pas strictement conformes aux spécifications OLE DB peuvent se comporter différemment. Par exemple, contrairement au fournisseur OLE DB Driver pour SQL Server, le fournisseur SQLOLEDB n’appliquait pas la règle selon laquelle les noms de paramètre doivent commencer par « \@ »pour les paramètres de résultat.  

-   OLE DB pilote pour SQL Server se comporte différemment de MDAC en ce qui concerne les échecs de connexion. Par exemple, MDAC retourne des valeurs de propriété mises en cache pour une connexion qui a échoué, alors qu’OLE DB Driver pour SQL Server signale une erreur à l’application appelante.  

-   OLE DB Driver pour SQL Server ne génère pas d’événements Visual Studio Analyzer, mais il génère à la place des événements de suivi Windows.  

-   OLE DB pilote pour SQL Server ne peut pas être utilisé avec Perfmon. Perfmon est un outil Windows qui peut être uniquement utilisé avec des noms de source de données (DSN) qui utilisent le pilote MDAC SQLODBC inclus avec Windows.  

-   Lorsque OLE DB pilote pour SQL Server est connecté à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures, l’erreur de serveur 16947 est retournée en SQL_ERROR. Cette erreur se produit lorsqu'une mise à jour ou une suppression positionnée ne parvient pas à mettre à jour ou à supprimer une ligne. Avec MDAC lors de la connexion à n'importe quelle version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'erreur de serveur 16947 est retournée en tant qu'avertissement (SQL_SUCCESS_WITH_INFO).  

-   OLE DB Driver pour SQL Server implémente l’interface **IDBDataSourceAdmin**, qui est une interface OLE DB facultative qui n’était pas précédemment implémentée, mais seule la méthode **CreateDataSource** de cette interface facultative est implémentée. [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  

-   Le fournisseur OLE DB Driver pour SQL Server retourne des synonymes dans les ensembles de lignes de schéma TABLES et TABLE_INFO, avec la valeur SYNONYM attribuée à TABLE_TYPE.  

-   Les valeurs de retour du type de données **varchar(max)** , **nvarchar(max)** , **varbinary(max)** , **xml**, **udt** ou de tout autre type d’objet volumineux ne peuvent pas être retournées aux versions de client antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Si vous souhaitez utiliser ces types comme valeurs de retour, vous devez utiliser OLE DB pilote pour SQL Server.  

-   Contrairement à OLE DB Driver pour SQL Server, MDAC permet l’exécution des instructions suivantes au démarrage de transactions manuelles et implicites. Elles doivent être exécutées en mode de validation automatique.  

    -   Tous les opérations de texte intégral (DDL d'index et de catalogue)  

    -   Toutes les opérations de base de données (create database, alter database, drop database)  

    -   Reconfiguration  

    -   Arrêter  

    -   Kill  

    -   Backup  

-   Lorsque des applications MDAC se connectent à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les types de données introduits dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] apparaissent en tant que types de données compatibles avec [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], comme indiqué dans le tableau suivant.  

    |Type SQL Server 2005|Type SQL Server 2000|  
    |--------------------------|--------------------------|  
    |**varchar(max)**|**text**|  
    |**nvarchar(max)**|**ntext**|  
    |**varbinary(max)**|**image**|  
    |**udt**|**varbinary**|  
    |**xml**|**ntext**|  

     Ce mappage de type affecte les valeurs retournées pour les métadonnées de colonne. Par exemple, une colonne de **texte** a une taille maximale de 2 147 483 647, mais OLE DB pilote pour SQL Server signale la taille maximale des colonnes de type **varchar (max)** comme 2 147 483 647 ou-1, en fonction de la plateforme.  

-   Pour des raisons de compatibilité descendante, OLE DB Driver pour SQL Server autorise l’ambiguïté dans les chaînes de connexion (par exemple, certains mots clés peuvent être spécifiés plusieurs fois et des mots clés en conflit peuvent être autorisés avec la résolution basée sur la position ou la précédence). Les versions ultérieures du pilote OLE DB pour SQL Server peuvent ne pas autoriser l’ambiguïté dans les chaînes de connexion. Lors de la modification d’applications, il est conseillé d’utiliser OLE DB Driver pour SQL Server pour éliminer toute dépendance vis-à-vis de l’ambiguïté des chaînes de connexion.  

-   Si vous utilisez un appel de OLE DB pour démarrer des transactions, il existe une différence de comportement entre OLE DB pilote pour SQL Server et MDAC. les transactions démarrent immédiatement avec OLE DB pilote pour SQL Server, mais les transactions commencent après le premier accès à la base de données à l’aide de MDAC. Cela peut affecter le comportement de procédures stockées et de lots, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nécessitant que @@TRANCOUNT soit le même entre le démarrage et la fin de l’exécution d’un lot ou d’une procédure stockée.  

-   Avec OLE DB pilote pour SQL Server, ITransactionLocal:: BeginTransaction entraîne le démarrage immédiat d’une transaction. Avec MDAC, le démarrage de la transaction était différé jusqu’à ce que l’application exécute une instruction qui exigeait une transaction en mode de transaction implicite. Pour plus d’informations, consultez [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../../t-sql/statements/set-implicit-transactions-transact-sql.md).  


 OLE DB pilote pour SQL Server et MDAC prennent en charge Read Committed transaction isolation à l’aide du contrôle de version de ligne, mais seul OLE DB pilote pour SQL Server prend en charge l’isolation des transactions de capture instantanée. (En termes de programmation, l'isolation de la transaction de lecture validée à l'aide du contrôle de version de ligne est la même chose que la transaction de lecture validée.)  

## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
