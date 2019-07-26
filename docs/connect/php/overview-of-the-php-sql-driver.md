---
title: Vue d’ensemble des pilotes Microsoft pour PHP pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 66559249-34c0-409d-b919-9b5bf0c4c9ec
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 25519d06df8b948d5cfc5d387029cf09beafc856
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936273"
---
# <a name="overview-of-the-microsoft-drivers-for-php-for-sql-server"></a>Vue d’ensemble des pilotes Microsoft pour PHP pour SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] est une extension PHP qui fournit l’accès aux données de SQL Server 2005 et des versions ultérieures, y compris Azure SQL Database. L’extension fournit une interface procédurale avec le pilote SQLSRV et une interface orientée objet avec le pilote PDO_SQLSRV pour accéder aux données dans toutes les versions de SQL Server, y compris Express, à partir de SQL Server 2005. La prise en charge des versions 3,1 et ultérieures des pilotes commence par SQL Server 2008. L’API [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] prend en charge l’authentification Windows, les transactions, la liaison de paramètre, la diffusion en continu, l’accès aux métadonnées et la gestion des erreurs.  
  
Pour utiliser le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], vous devez disposer de la version appropriée de SQL Server Native Client ou du pilote Microsoft ODBC installé sur le même ordinateur que PHP est en cours d’exécution.  Pour plus d’informations, consultez [Configuration système requise pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|---------|---------------|  
| ![Télécharger-DownArrow-cercle](../../ssdt/media/download.png)[pour télécharger les pilotes pour PHP pour SQL Server](download-drivers-php-sql-server.md) | Liens de téléchargement des pilotes Microsoft pour PHP pour SQL Server. |
|[Notes de publication des pilotes Microsoft pour PHP pour SQL Server](../../connect/php/release-notes-php-sql-driver.md)|Présente les fonctionnalités ajoutées pour les versions 4.0, 3.2, 3.1, 3.0 et 2.0.|  
|[Ressources de support sur les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/support-resources-for-the-php-sql-driver.md)|Fournit des liens vers des ressources qui peuvent être utiles quand vous développez des applications qui utilisent [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].|  
|[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)|Fournit des informations qui peuvent être utiles quand vous exécutez les exemples de code dans cette documentation.|  
| &nbsp; | &nbsp; |

## <a name="reference"></a>Référence

[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Référence de pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
[Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  

## <a name="see-also"></a>Voir aussi

[Bien démarrer avec les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Guide de programmation pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Exemple d’application &#40;pilote SQLSRV&#41;](../../connect/php/example-application-sqlsrv-driver.md)
