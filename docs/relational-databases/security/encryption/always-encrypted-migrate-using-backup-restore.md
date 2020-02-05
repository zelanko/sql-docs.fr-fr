---
title: Sauvegarder et restaurer des bases de données avec Always Encrypted | Microsoft Docs
ms.custom: ''
ms.date: 10/30/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
ms.assetid: 29816a41-f105-4414-8be1-070675d62e84
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9176052b413293d25acd7696701e4f118adba03f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "73595724"
---
# <a name="backup-and-restore-databases-using-always-encrypted"></a>Sauvegarder et restaurer des bases de données avec Always Encrypted 
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Cet article explique comment sauvegarder et restaurer une base de données contenant des colonnes protégées avec [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md).

Quand vous sauvegardez une base de données, le fichier de sauvegarde résultant contient des données chiffrées stockées dans les colonnes chiffrées et toutes les métadonnées pour les clés Always Encrypted.

Quand vous restaurez une base de données, toutes les données chiffrées et toutes les métadonnées pour les clés Always Encrypted sont restaurées. 

Si vous avez restauré la base de données sur un autre serveur ou sous un autre nom, vous n’avez rien de spécial à faire pour permettre à l’application d’interroger les données chiffrées dans la base de données cible, car les clés sont identiques dans les deux bases de données.

Pour plus d’informations sur la façon de sauvegarder et de restaurer une base de données, consultez :
- [Vue d’ensemble de la sauvegarde (SQL Server)](../../backup-restore/backup-overview-sql-server.md)
- [Restaurer une base de données sur une instance managée](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started-restore)

## <a name="next-steps"></a>Étapes suivantes
- [Interroger des colonnes en utilisant Always Encrypted avec SQL Server Management Studio](always-encrypted-query-columns-ssms.md)
- [Développer des applications en utilisant Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-client-development.md) 

## <a name="see-also"></a>Voir aussi
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Exporter et importer des bases de données avec Always Encrypted](always-encrypted-migrate-using-bacpac.md)
- [Migrer des données à partir ou à destination de colonnes à l’aide d’Always Encrypted avec l’Assistant Importation et exportation SQL Server](always-encrypted-migrate-using-import-export-wizard.md)
- [Charger en bloc des données chiffrées dans des colonnes avec Always Encrypted](migrate-sensitive-data-protected-by-always-encrypted.md)
