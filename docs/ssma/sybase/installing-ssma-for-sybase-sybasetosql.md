---
title: Installation de SSMA pour SAP ASE (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b859c3b9841945241ac0ec9c5238a479a5ba3343
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63302819"
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>Installation de SSMA pour SAP ASE (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) pour SAP Adaptive Server Enterprise (ASE) se compose d’une application cliente qui permet d’effectuer une migration à partir de SAP ASE pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. Il contient également un pack d’extension qui prend en charge la migration des données et l’utilisation des fonctions du système ASE dans vos bases de données migrées.  
  
Installer l’application cliente sur l’ordinateur à partir duquel vous envisagez d’effectuer les étapes de migration. Installer les fichiers de pack d’extension sur l’ordinateur qui est en cours d’exécution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur lequel les bases de données migrées doivent être hébergés.  
  
## <a name="upgrading-ssma-for-sap-ase"></a>La mise à niveau de SSMA pour SAP ASE  
Si vous souhaitez mettre à niveau vers une version ultérieure de SSMA pour SAP ASE, vous devez d’abord désinstaller le client et le pack d’extension de serveur. Puis installez la version plus récente.  
  
Si vous ouvrez un projet à partir d’une version antérieure de SSMA pour SAP ASE, SSMA vous demande si vous souhaitez convertir le projet vers la version plus récente. Cliquez sur **Oui** pour travailler avec le projet dans la version la plus récente de SSMA.  
  
## <a name="contents"></a>Sommaire  
  
|Article|Description|  
|---------|---------------|  
|[Installation de SSMA pour SAP ASE Client &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Fournit des informations et des instructions d’installation de SSMA pour le client de SAP ASE.|  
|[Installation des composants SSMA sur SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Fournit des informations et des instructions pour installer le pack d’extension sur les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Suppression de SSMA pour les composants SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Fournit des instructions sur la désinstallation du client de pack de programme et l’extension.|  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration SAP ASE pour SQL Server - Azure SQL Database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
