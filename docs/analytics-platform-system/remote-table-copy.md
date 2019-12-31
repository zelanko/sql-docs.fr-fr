---
title: Copie de table distante
description: Utilisation d’une copie de table distante dans Analytics Platform System Parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ecbbdced731e940de46dbde4a65adc486f602c2f
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400481"
---
# <a name="remote-table-copy"></a>Copie de table distante
Décrit comment utiliser la fonctionnalité de copie de table distante pour copier des tables à partir de SQL Server PDW bases de données vers des bases de données SMP à distance (sans Appliance) SQL Server. Utilisez la copie de table distante pour activer les scénarios Hub et spoke pour SQL Server PDW.  
  
## <a name="BasicsPDE"></a>Comprendre la copie de table distante pour SQL Server PDW  
La copie de table distante est une fonctionnalité de SQL Server PDW qui active des scénarios Hub et spoke en copiant les résultats d’une instruction SQL SELECT dans une table d’une base de données SMP. La copie de la table distante est lancée avec l’instruction [Create Remote table As Select](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) .  
  
## <a name="BasicsPrerequisites"></a>Conditions requises pour l’utilisation de la copie de table distante  
Vous pouvez utiliser la copie de table distante pour copier des tables d’SQL Server PDW vers une base de données SQL Server lorsque ces conditions sont remplies :  
  
-   La base de données de destination doit être une instance de Microsoft® SQL Server® qui s’exécute sur un système Microsoft Windows® capable de se connecter à l’appareil SQL Server PDW, mais qui ne réside pas sur un serveur au sein de l’appliance. La SQL Server distante peut être connectée au SQL Server PDW à l’aide du réseau InfiniBand ou via le réseau Ethernet.  
  
-   Vous devez sélectionner les données à copier à l’aide d’une seule instruction [Select](../t-sql/queries/select-transact-sql.md) valide SQL Server PDW Select.  
  
-   Le serveur de destination doit être un serveur non-appliance. Les données ne peuvent pas être copiées directement d’un appareil vers un autre à l’aide des instructions de cette rubrique.  
  
-   Le serveur de destination doit être accessible à tous les nœuds sur le réseau InfiniBand de l’appliance.  
  
## <a name="ConfigureRemote"></a>Configurer la copie de table distante  
Pour utiliser la copie de table distante, vous devez acheter et configurer un serveur Windows Server, configurer SQL Server sur Windows Server et configurer SQL Server PDW. Utilisez les liens suivants pour effectuer ces trois étapes de configuration.  
  
1.  [Configurer un système Windows externe pour recevoir des copies de tables distantes à l’aide de InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)  
  
2.  [Configurer un SQL Server SMP externe pour recevoir des copies de tables distantes](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)  
  
3.  [Configurer SQL Server PDW pour les copies de tables distantes](configure-sql-server-pdw-for-remote-table-copies.md)  
  
## <a name="PerformRemote"></a>Effectuer une copie de table distante  
Pour effectuer une copie de table distante, utilisez l’instruction [Create Remote table As Select](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) SQL. Des exemples sont fournis avec la rubrique créer une TABLE distante.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
