---
title: Connexion au serveur
description: Découvrez les différentes méthodes de connexion à la base de données à l’aide des Pilotes Microsoft pour PHP pour SQL Server.
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c251a239-e0bd-4f45-9207-b76651072dd0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5a2ec027a72bd96b567b08639568b6ead8e5dc64
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87410975"
---
# <a name="connecting-to-the-server"></a>Connexion au serveur
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Les rubriques de cette section décrivent les options et les procédures de connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] peut se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’authentification Windows ou de l’authentification SQL Server. Par défaut, [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] essaie de se connecter au serveur à l’aide de l’authentification Windows.  

## <a name="in-this-section"></a>Dans cette section  

|Rubrique|Description|  
|---------|---------------|  
|[Procédure : Se connecter avec l’authentification Windows](../../connect/php/how-to-connect-using-windows-authentication.md)|Décrit comment établir une connexion à l’aide de l’authentification Windows.|  
|[Procédure : Se connecter avec l’authentification SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md)|Décrit comment établir une connexion à l’aide de l’authentification SQL Server.|  
|[Procédure : Se connecter à l’aide de l’authentification Azure Active Directory](../../connect/php/azure-active-directory.md)|Explique comment définir le mode d’authentification et se connecter avec des identités Azure Active Directory.|  
|[Procédure : Se connecter sur un port spécifié](../../connect/php/how-to-connect-on-a-specified-port.md)|Décrit comment se connecter au serveur sur un port spécifique.|  
|[Regroupement de connexions](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)|Fournit des informations sur le regroupement de connexions dans le pilote.|  
|[Procédure : Désactiver MARS (Multiple Active Result Set)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md)|Décrit comment désactiver la fonctionnalité MARS pendant une connexion.|  
|[Options de connexion](../../connect/php/connection-options.md)|Répertorie les options autorisées dans le tableau associatif qui contient les attributs de connexion.|  
|[Prise en charge de la base de données locale](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)|Décrit la prise en charge par [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] de la fonctionnalité Base de données locale, ajoutée dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].|  
|[Prise en charge des fonctionnalités de récupération d’urgence/haute disponibilité](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)|Explique comment votre application peut être configurée pour tirer parti des fonctionnalités de récupération d'urgence haute disponibilité, ajoutées dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].|  
|[Connexion à Microsoft Azure SQL Database](../../connect/php/connecting-to-microsoft-azure-sql-database.md)|Traite de la connexion à une base de données Azure SQL Database.|  
|[Résilience de connexion](../../connect/php/connection-resiliency.md)|Décrit la fonctionnalité de résilience de connexion qui rétablit les connexions interrompues.|  

## <a name="see-also"></a>Voir aussi  
[Guide de programmation pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Exemple d’application &#40;pilote SQLSRV&#41;](../../connect/php/example-application-sqlsrv-driver.md)  
