---
title: Copie de la table distante - Parallel Data Warehouse | Microsoft Docs
description: À l’aide de la copie de la table distante dans Analytique Platform System Parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 28bd5deda25650d36467281ccbffa7b666f4c695
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960202"
---
# <a name="remote-table-copy"></a>Copie de la Table distante
Décrit comment utiliser la fonctionnalité de copie de table distante pour copier des tables de bases de données SQL Server PDW aux bases de données de SQL Server SMP (non-appliance) à distance. Utiliser la copie de la table distante permet des scénarios hub- and -spoke pour SQL Server PDW.  
  
## <a name="BasicsPDE"></a>Comprendre la copie de la Table à distance pour SQL Server PDW  
Copie de la table distante est une fonctionnalité de SQL Server PDW qui permet des scénarios de Hub and Spoke en copiant les résultats d’une instruction SQL SELECT sur une table dans une base de données SMP. La copie de la table distante est initialisée avec le [créer REMOTE TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) instruction.  
  
## <a name="BasicsPrerequisites"></a>Configuration requise pour utiliser la copie de la Table distante  
Vous pouvez utiliser la table distante copie pour copier les tables à partir de SQL Server PDW pour une base de données SQL Server lorsque ces conditions sont remplies :  
  
-   La base de données de destination doit être une instance de Microsoft® SQL Server® qui s’exécute sur un système Microsoft Windows® qui peut se connecter à l’appliance SQL Server PDW, mais ne réside pas sur un serveur au sein de l’appliance. Le serveur SQL distant peut être connecté à l’ordinateur SQL Server PDW utilisant le réseau InfiniBand ou via le réseau Ethernet.  
  
-   Les données à copier doivent être sélectionnées à l’aide d’un unique valide SQL Server PDW [sélectionnez](../t-sql/queries/select-transact-sql.md) instruction.  
  
-   Le serveur de destination doit être un serveur non-appliance. Données ne peut pas être copiées directement à partir d’une appliance vers une autre en suivant les instructions dans cette rubrique.  
  
-   Le serveur de destination doit être accessible à tous les nœuds sur le réseau Infiniband de l’application.  
  
## <a name="ConfigureRemote"></a>Configurer la copie de la Table distante  
Pour utiliser la copie de la table distante, vous devez acheter et configurer un serveur Windows, configurez SQL Server sur le serveur Windows et configurer SQL Server PDW. Utilisez les liens suivants pour effectuer ces trois étapes de configuration.  
  
1.  [Configuration d’un système Windows externe pour recevoir une copie de Table distante à l’aide d’InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)  
  
2.  [Configurer un serveur SQL de SMP externe pour recevoir une copie de la Table distante](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)  
  
3.  [Configurer SQL Server PDW pour les Copies de la Table distante](configure-sql-server-pdw-for-remote-table-copies.md)  
  
## <a name="PerformRemote"></a>Effectuer une copie de la Table distante  
Pour effectuer une copie de la table distante, utilisez le [créer REMOTE TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) instruction SQL. Exemples sont inclus dans la rubrique CREATE REMOTE TABLE.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
