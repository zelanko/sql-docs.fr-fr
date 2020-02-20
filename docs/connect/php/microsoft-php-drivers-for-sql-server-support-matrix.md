---
title: Matrice de prise en charge des pilotes PHP pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: genemi
manager: ''
ms.openlocfilehash: c542a77c3a7cfbbe9c54786116e3e9e800a3dda0
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76917806"
---
# <a name="microsoft-php-drivers-for-sql-server-support-matrix"></a>Matrice de prise en charge des pilotes PHP pour SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette page contient la matrice de support et la politique de support des pilotes Microsoft PHP pour SQL Server.

## <a name="microsoft-php-drivers-support-lifecycle-matrix-and-policy"></a>Matrice et politique de support des pilotes Microsoft PHP

La politique de support de Microsoft fournit des informations transparentes et prévisibles concernant la politique de support des produits Microsoft. Les versions 3.x, 4.x et 5.x des pilotes PHP bénéficient de cinq ans de support standard à partir de la date de publication du pilote. Le support standard est défini sur le [site web de la politique de support de Microsoft](https://support.microsoft.com/lifecycle).

Les options de support étendu et personnalisé ne sont pas disponibles pour les pilotes Microsoft PHP.

Les pilotes Microsoft PHP suivants bénéficient d’un support jusqu’à la date de fin de support indiquée.

|Nom du pilote|Version de package du pilote|Fin du support standard|
|-|:-:|-|
|Microsoft PHP Drivers 5.8 pour SQL Server|5.8|31 janvier 2025|
|Microsoft PHP Drivers 5.6 pour SQL Server|5.6|21 février 2024|
|Microsoft PHP Drivers 5.3 pour SQL Server|5.3|20 juillet 2023|
|Microsoft PHP Drivers 5.2 pour SQL Server|5.2|9 février 2023|
|Microsoft PHP Drivers 4.3 pour SQL Server|4.3|6 juillet 2022|
|Microsoft PHP Drivers 4.0 pour SQL Server|4.0|11 juillet 2021|
|Microsoft PHP Drivers 3.2 pour SQL Server|3.2|9 mars 2020|
| &nbsp; | &nbsp; | &nbsp; |

Les pilotes Microsoft PHP suivants ne sont plus supportés.

|Nom du pilote|Version de package du pilote|Fin du support standard|
|-|:-:|-|
|Microsoft PHP Drivers 3.1 pour SQL Server|3.1|12 décembre 2019|
|Microsoft PHP Drivers 3.0 pour SQL Server|3.0|6 mars 2017|
|Microsoft PHP Drivers 2.0 pour SQL Server|2|10 août 2015|
|Microsoft PHP Drivers 1.0 pour SQL Server|1.0|28 avril 2014|
| &nbsp; | &nbsp; | &nbsp; |

## <a name="sql-server-version-certified-compatibility"></a>Compatibilité certifiée de la version SQL Server
 La matrice suivante répertorie les versions de SQL Server qui ont été testées et certifiées comme compatibles avec la version du pilote correspondante. Nous nous efforçons de maintenir une compatibilité descendante avec les versions de pilote précédentes, mais seul le dernier pilote pris en charge est testé et certifié avec les nouvelles versions de SQL Server, à mesure que SQL Server est publié.

|PHP pour le pilote SQL Server version &#8594;<br />&#8595; Version de SQL Server|5.8|5.6|5.3|5.2|4.3|4.0|3.2|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Azure SQL Managed Instance|O|O|O|O|O| | |
|Azure SQL Data Warehouse.|O|O|O|O|O| | |
|SQL Server 2019         |O| | | | | | |
|SQL Server 2017         |O|O|O|O|O| | |
|SQL Server 2016         |O|O|O|O|O|O| |
|SQL Server 2014         |O|O|O|O|O|O|O|
|SQL Server 2012         |O|O|O|O|O|O|O|
|SQL Server 2008 R2      | |O|O|O|O|O|O|
|SQL Server 2008         | | | | | |O|O|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="php-version-support"></a>Prise en charge de la version de PHP

Les versions suivantes de PHP sont prises en charge avec la version répertoriée des pilotes Microsoft PHP :

|PHP pour le pilote SQL Server version &#8594;<br />&#8595; Version de PHP|5.8|5.6|5.3|5.2|4.3|4.0|3.2|
|:---:|---|---|---|---|---|---|---|
|7.4|7.4.0+          |                |                |                |       |        |        |
|7.3|7.3.0+          |7.3.0+          |                |                |       |        |        |
|7.2|7.2 +<sup>1</sup>|7.2 +<sup>1</sup>|7.2 +<sup>1</sup>|7.2 +<sup>1</sup>|       |        |        |
|7.1|                |7.1.0+          |7.1.0+          |7.1.0+          |7.1.0+ |        |        |
|7.0|                |                |7.0.0+          |7.0.0+          |7.0.0+ |7.0.0+  |        |
|5.6|                |                |                |                |       |        |5.6.4+  |
|5.5|                |                |                |                |       |        |5.5.16+ |
|5.4|                |                |                |                |       |        |5.4.32  |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

1. Les versions 7.2.1 et ultérieures sont prises en charge sur Windows, tandis que les versions 7.2.0 et ultérieures sont prises en charge sur Linux et macOS.

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

Les versions suivantes du système d'exploitation Windows sont prises en charge avec la version répertoriée des pilotes Microsoft PHP :

|PHP pour le pilote SQL Server version &#8594;<br />&#8595; Système d’exploitation|5.8|5.6|5.3|5.2|4.3|4.0|3.2|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Windows Server 2019                 |O  |O  |   |   |   |   |   |
|Windows Server 2016                 |O  |O  |O  |O  |O  |   |   |
|Windows Server 2012 R2              |O  |O  |O  |O  |O  |O  |O  |
|Windows Server 2012                 |O  |O  |O  |O  |O  |O  |O  |
|Windows Server 2008 R2 SP1          |   |   |   |   |   |O  |O  |
|Windows Server 2008 R2              |   |   |   |   |   |   |   |
|Windows Server 2008 SP2             |   |   |   |   |   |O  |O  |
|Windows 10                          |O  |O  |O  |O  |O  |O  |   |
|Windows 8.1                         |O  |O  |O  |O  |O  |O  |O  |
|Windows 8                           |   |   |   |   |O  |O  |O  |
|Windows 7 SP1                       |   |   |   |   |   |O  |O  |
|Windows Vista SP2                   |   |   |   |   |   |O  |O  |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

Les versions suivantes des systèmes d'exploitation Linux et Mac (64 bits uniquement) sont prises en charge avec la version répertoriée des pilotes Microsoft PHP :

|PHP pour le pilote SQL Server version &#8594;<br />&#8595; Système d’exploitation|5.8|5.6|5.3|5.2|4.3|4.0|3.2|
|--|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Ubuntu 19.10 (64 bits)               |O  |   |   |   |   |   |   |
|Ubuntu 18.10 (64 bits)               |   |O  |   |   |   |   |   |
|Ubuntu 18.04 (64 bits)               |O  |O  |O  |   |   |   |   |
|Ubuntu 17.10 (64 bits)               |   |   |O  |O  |   |   |   |
|Ubuntu 16.04 (64 bits)               |O  |O  |O  |O  |O  |O  |   |
|Ubuntu 15.10 (64 bits)               |   |   |   |   |O  |   |   |
|Ubuntu 15.04 (64 bits)               |   |   |   |   |   |O  |   |
|Debian 10 (64 bits)                  |O  |   |   |   |   |   |   |
|Debian 9 (64 bits)                   |O  |O  |O  |O  |   |   |   |
|Debian 8 (64 bits)                   |O  |O  |O  |O  |O  |   |   |
|Red Hat Enterprise Linux 8 (64 bits) |O  |   |   |   |   |   |   |
|Red Hat Enterprise Linux 7 (64-bit) |O  |O  |O  |O  |O  |O  |   |
|Red Hat Enterprise Linux 15 (64 bits)   |O  |O  |   |   |   |   |   |
|Red Hat Enterprise Linux 12 (64 bits)   |O  |O  |O  |O  |   |   |   |
|Alpine Linux 3.11 (64 bits)<sup>1</sup>|O  |   |   |   |   |   |   |
|macOS Catalina (64 bits)             |O  |   |   |   |   |   |   |
|macOS Mojave (64 bits)               |O  |O  |   |   |   |   |   |
|macOS High Sierra (64 bits)          |O  |O  |O  |   |   |   |   |
|macOS Sierra (64 bits)               |   |O  |O  |O  |O  |   |   |
|macOS El Capitan (64 bits)           |   |   |O  |O  |O  |   |   |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

<sup>1</sup> La prise en charge d’Alpine Linux est expérimentale pour la version 5.8.

## <a name="see-also"></a>Voir aussi

[Notes de publication](../../connect/php/release-notes-php-sql-driver.md)

[Ressources de support](../../connect/php/support-resources-for-the-php-sql-driver.md)

[Configuration requise](../../connect/php/system-requirements-for-the-php-sql-driver.md)
