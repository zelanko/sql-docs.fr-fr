---
title: OLE DB Driver pour SQL Server fonctionnalités | Microsoft Docs
description: Fonctionnalités OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], features
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 24a91e845d26b4e01b8e90c60e78c9402e1ef73a
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036319"
---
# <a name="ole-db-driver-for-sql-server-features"></a>Fonctionnalités OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  En plus de l’exposition des fonctionnalités Windows (anciennement Microsoft) Data Access Components (WDAC), OLE DB Driver pour SQL Server implémente plusieurs autres fonctionnalités pour tirer parti des fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section    
 [Utilisation de la mise en miroir de bases de données](../../oledb/features/using-database-mirroring.md)  
 Explique comment OLE DB Driver pour SQL Server prend en charge l’utilisation de bases de données mises en miroir, à savoir la capacité de conserver une copie, ou un miroir, d’une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur un serveur de secours.  
  
 [Exécution d’opérations asynchrones](../../oledb/features/performing-asynchronous-operations.md)  
 Explique comment OLE DB Driver pour SQL Server prend en charge les opérations asynchrones, à savoir la capacité d’un retour immédiat sans blocage sur le thread appelant.  
  
 [Utilisation de MARS &#40;Multiple Active Result Sets&#41;](../../oledb/features/using-multiple-active-result-sets-mars.md)  
 Explique comment OLE DB Driver pour SQL Server prend en charge les jeux de résultats actifs multiples (MARS). MARS permet d'exécuter et de recevoir plusieurs jeux de résultats à l'aide d'une seule connexion de base de données.  
  
 [Utilisation de types de données XML](../../oledb/features/using-xml-data-types.md)  
 Explique comment OLE DB Driver pour SQL Server prend en charge le type de données XML, qui peut être utilisé comme type de colonne, type de variable, type de paramètre ou type de retour de fonction.  
  
 [Utilisation de types définis par l’utilisateur](../../oledb/features/using-user-defined-types.md)  
 Explique comment OLE DB Driver pour SQL Server prend en charge UDT, qui étend le système de types SQL en permettant de stocker les objets et les structures de données personnalisées dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Utilisation de types de valeur élevée](../../oledb/features/using-large-value-types.md)  
 Explique comment OLE DB Driver pour SQL Server prend en charge les types de données de valeur élevée, qui sont des types de données objet volumineux (LOB).  
  
 [Changement des mots de passe par programmation](../../oledb/features/changing-passwords-programmatically.md)  
 Explique comment OLE DB Driver pour SQL Server prend en charge la gestion des mots de passe périmés afin que les mots de passe puissent désormais être modifiés sur le client sans intervention de l’administrateur.  
  
 [Utilisation du niveau d’isolement de capture instantanée](../../oledb/features/working-with-snapshot-isolation.md)  
 Explique comment OLE DB Driver pour SQL Server prend en charge l’amélioration apportée au contrôle de version de ligne qui optimise les performances de la base de données en évitant les scénarios de blocage du lecteur/enregistreur.  
  
 [Utilisation de notifications de requêtes](../../oledb/features/working-with-query-notifications.md)  
 Explique comment OLE DB Driver pour SQL Server prend en charge la notification des consommateurs sur la modification de l’ensemble de lignes.  
  
 [Exécution d'opérations de copie en bloc](../../oledb/features/performing-bulk-copy-operations.md)  
 Explique comment OLE DB Driver pour SQL Server prend en charge les opérations de copie en bloc qui autorisent le transfert d’importantes quantités de données vers ou depuis une table ou une vue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Utilisation du chiffrement sans validation](../../oledb/features/using-encryption-without-validation.md)  
 Explique comment utiliser OLE DB Driver pour SQL Server pour chiffrer les données envoyées au serveur sans validation du certificat.  
  
 [Paramètres table &#40;OLE DB Driver pour SQL Server&#41;](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md)  
 Traite le pilote OLE DB pour la prise en charge de SQL Server pour les paramètres table.  
  
 [Types CLR volumineux définis par l’utilisateur](../../oledb/features/large-clr-user-defined-types.md)  
 Explique la prise en charge des types UDT volumineux du CLR.  
  
 [Prise en charge de FILESTREAM](../../oledb/features/filestream-support.md)  
 Décrit le pilote OLE DB pour la prise en charge de SQL Server pour la fonctionnalité FILESTREAM améliorée.  
  
 [Prise en charge des noms de principal du service &#40;SPN&#41; dans les connexions clientes](../../oledb/features/service-principal-name-spn-support-in-client-connections.md)  
 Explique comment la prise en charge des noms de principaux du service a été étendue pour permettre l'authentification mutuelle à travers l'ensemble des protocoles.  
  
 [Prise en charge des colonnes éparses dans OLE DB Driver pour SQL Server](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md)  
 Décrit le pilote OLE DB pour la prise en charge de SQL Server pour les colonnes éparses.  
  
 [Améliorations des types de données date et heure](../../oledb/features/date-and-time-improvements.md)  
 Décrit la prise en charge par OLE DB Driver pour SQL Server pour les types de données de date et d’heure.  
  
 [Détection des métadonnées](../../oledb/features/metadata-discovery.md)  
 Décrit les améliorations apportées à la découverte des métadonnées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Prise en charge d’UTF-16 dans OLE DB Driver pour SQL Server](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  
 Décrit un changement de comportement introduit dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. Si vous fournissez une mémoire tampon de longueur fixe lors de la liaison d’un résultat de colonne ou d’un paramètre de sortie et que le caractère **wchar** écrit dans la mémoire tampon avant le caractère de fin est un point de code de substitut étendu d’une paire de substitution, et si le caractère **wchar** suivant est un point de code de substitut faible, OLE DB Driver pour SQL Server n’ajoutera pas le point de code de substitut étendu à la mémoire tampon.  
  
 [Prise en charge de la récupération d’urgence et de la haute disponibilité par OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  
 Explique comment votre application peut être configurée pour tirer parti des fonctionnalités de récupération d'urgence haute disponibilité, ajoutées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Accès aux informations de diagnostic dans le journal des événements étendus](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  
 Présente les améliorations apportées à OLE DB Driver pour SQL Server et au suivi de données qui vous donne accès aux informations de diagnostic dans la mémoire tampon en anneau et le journal XEvents.  
  
 [Prise en charge de la base de données locale par OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  
 Décrit le pilote OLE DB pour la prise en charge de SQL Server pour la fonctionnalité de base de données locale.  
  
## <a name="see-also"></a> Voir aussi  
 [OLE DB Driver for SQL Server](../../oledb/oledb-driver-for-sql-server.md)      
 [Rubriques de procédures OLE DB](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)   
 [Installation d’OLE DB Driver pour SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md)  
  
  
