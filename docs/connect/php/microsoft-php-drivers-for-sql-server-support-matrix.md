---
title: Matrice de Support Microsoft Drivers for PHP for SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: genemi
manager: ''
ms.openlocfilehash: 0790d2cc0497ef2912f96cd4679e4541fc9b2262
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63180275"
---
# <a name="microsoft-php-drivers-for-sql-server-support-matrix"></a>Pilotes Microsoft PHP pour SQL Server Support Matrix

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette page contient la matrice de support et la politique de support des pilotes Microsoft PHP pour SQL Server.

## <a name="microsoft-php-drivers-support-lifecycle-matrix-and-policy"></a>Matrice de cycle de vie de prise en charge de pilotes Microsoft PHP et stratégie

La politique de support de Microsoft fournit des informations transparentes et prévisibles concernant la politique de support des produits Microsoft. Les versions 3.x, 4.x et 5.x des pilotes PHP bénéficient de cinq ans de support standard à partir de la date de publication du pilote. Le support standard est défini sur le [site web de la politique de support de Microsoft](https://support.microsoft.com/lifecycle).

Les options de support étendu et personnalisé ne sont pas disponibles pour les pilotes Microsoft PHP.

Les pilotes Microsoft PHP suivants bénéficient d’un support jusqu’à la date de fin de support indiquée.

|Nom du pilote|Version de package du pilote|Fin du support standard|
|-|:-:|-|
|Microsoft PHP Drivers 5.6 pour SQL Server|5.6|21 février 2024|
|Microsoft PHP Drivers 5.3 pour SQL Server|5.3|20 juillet 2023|
|Microsoft PHP Drivers 5.2 pour SQL Server|5.2|9 février 2023|
|Microsoft PHP Drivers 4.3 pour SQL Server|4.3|6 juillet 2022|
|Microsoft PHP Drivers 4.0 pour SQL Server|4.0|11 juillet 2021|
|Microsoft PHP Drivers 3.2 pour SQL Server|3.2|9 mars 2020|
|Microsoft PHP Drivers 3.1 pour SQL Server|3.1|12 décembre 2019|
| &nbsp; | &nbsp; | &nbsp; |

Les pilotes Microsoft PHP suivants ne sont plus supportés.

|Nom du pilote|Version de package du pilote|Fin du support standard|
|-|:-:|-|
|Microsoft PHP Drivers 3.0 pour SQL Server|3|6 mars 2017|
|Microsoft PHP Drivers 2.0 pour SQL Server|2|10 août 2015|
|Microsoft PHP Drivers 1.0 pour SQL Server|1.0|28 avril 2014|
| &nbsp; | &nbsp; | &nbsp; |

## <a name="sql-server-version-certified-compatibility"></a>Certifié de compatibilité de la Version de SQL Server
 Le tableau suivant répertorie les versions de SQL Server qui ont été testées et certifiées comme étant compatibles avec la version du pilote correspondant. Nous nous efforçons d’assurer la compatibilité descendante avec les versions précédentes du pilote, mais uniquement le dernier pilote pris en charge est testé et certifié avec les nouvelles versions de SQL Server, comme SQL Server est lancé.

|PHP pour la version du pilote SQL Server&#8594;<br />&#8595; Version de SQL Server|5.6|5.3|5.2|4.3|4.0|3.2|3.1|3|2|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Azure SQL Managed Instance<br/> (Préversion privée étendue)|O|O|O|O| | | | | |
|Azure SQL Data Warehouse.|O|O|O|O| | | | | |
|SQL Server 2017         |O|O|O|O| | | | | |
|SQL Server 2016         |O|O|O|O|O| | | | |
|SQL Server 2014         |O|O|O|O|O|O|O| | |
|SQL Server 2012         |O|O|O|O|O|O|O|O| |
|SQL Server 2008 R2      |O|O|O|O|O|O|O|O|O|
|SQL Server 2008         | | | | |O|O|O|O|O|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="php-version-support"></a>Prise en charge de la version de PHP

Les versions suivantes de PHP sont pris en charge avec la version répertoriée des pilotes Microsoft PHP :

|PHP pour la version du pilote SQL Server&#8594;<br />&#8595; Version de PHP|5.6|5.3|5.2|4.3|4.0|3.2|3.1|3|2|
|:---:|---|---|---|---|---|---|---|---|---|
|7.3|7.3.0+          |                |                |       |       | | | | |
|7.2|7.2 +<sup>1</sup>|7.2 +<sup>1</sup>|7.2 +<sup>1</sup>|       |       | | | | |
|7.1|7.1.0+          |7.1.0+          |7.1.0+          |7.1.0+ |       |        |        |        |        |
|7.0|                |7.0.0+          |7.0.0+          |7.0.0+ |7.0.0+ |        |        |        |        |
|5.6|                |                |                |       |       |5.6.4+  |        |        |        |
|5.5|                |                |                |       |       |5.5.16+ |5.5.16+ |        |        |
|5.4|                |                |                |       |       |5.4.32  |5.4.32  |5.4.32  |        |
|5.3|                |                |                |       |       |        |        |5.3.0   |5.3.0   |
|5.2|                |                |                |       |       |        |        |        |5.2.4<br />5.2.13|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

1. Versions 7.2.1 et plus tard sont pris en charge sur Windows, tout en versions 7.2.0 et versions ultérieures sont pris en charge sur Linux et macOS.

## <a name="supported-operating-systems"></a>Systèmes d'exploitation pris en charge

Les versions de système d’exploitation Windows suivantes sont pris en charge avec la version répertoriée des pilotes Microsoft PHP :

|PHP pour la version du pilote SQL Server&#8594;<br />&#8595; Système d’exploitation|5.6|5.3|5.2|4.3|4.0|3.2|3.1|3|2|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Windows Server 2016                 |O  |O  |O  |O  |   |   |   |   |   |
|Windows Server 2012 R2              |O  |O  |O  |O  |O  |O  |O  |   |   |
|Windows Server 2012                 |O  |O  |O  |O  |O  |O  |O  |   |   |
|Windows Server 2008 R2 SP1          |   |   |   |   |O  |O  |O  |O  |   |
|Windows Server 2008 R2              |   |   |   |   |   |   |   |   |O  |
|Windows Server 2008 SP2             |   |   |   |   |O  |O  |O  |O  |   |
|Windows Server 2008                 |   |   |   |   |   |   |   |   |O  |
|Windows Server 2003 SP1             |   |   |   |   |   |   |   |   |O  |
|Windows 10                          |O  |O  |O  |O  |O  |   |   |   |   |
|Windows 8.1                         |O  |O  |O  |O  |O  |O  |O  |   |   |
|Windows 8                           |   |   |   |O  |O  |O  |O  |   |   |
|Windows 7 SP1                       |   |   |   |   |O  |O  |O  |O  |   |
|Windows Vista SP2                   |   |   |   |   |O  |O  |O  |O  |O  |
|Windows XP SP3                      |   |   |   |   |   |   |   |   |O  |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

Linux et Mac versions (64 bits uniquement) des système d’exploitation suivants sont pris en charge avec la version répertoriée des pilotes Microsoft PHP :

|PHP pour la version du pilote SQL Server&#8594;<br />&#8595; Système d’exploitation|5.6|5.3|5.2|4.3|4.0|3.2|3.1|3|2|
|--|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Ubuntu 18.10 (64 bits)               |O  |   |   |   |   |   |   |   |   |
|Ubuntu 18.04 (64 bits)               |O  |O  |   |   |   |   |   |   |   |
|Ubuntu 17.10 (64 bits)               |   |O  |O  |   |   |   |   |   |   |
|Ubuntu 16.04 (64 bits)               |O  |O  |O  |O  |O  |   |   |   |   |
|Ubuntu 15.10 (64 bits)               |   |   |   |O  |   |   |   |   |   |
|Ubuntu 15.04 (64 bits)               |   |   |   |   |O  |   |   |   |   |
|Debian 9 (64 bits)                   |O  |O  |O  |   |   |   |   |   |   |
|Debian 8 (64 bits)                   |O  |O  |O  |O  |   |   |   |   |   |
|Red Hat Enterprise Linux 7 (64-bit) |O  |O  |O  |O  |O  |   |   |   |   |
|SuSE Enterprise Linux 15 (64 bits)   |O  |   |   |   |   |   |   |   |   |
|SuSE Enterprise Linux 12 (64 bits)   |O  |O  |O  |   |   |   |   |   |   |
|macOS Mojave (64 bits)               |O  |   |   |   |   |   |   |   |   |
|macOS High Sierra (64 bits)          |O  |O  |   |   |   |   |   |   |   |
|macOS Sierra (64 bits)               |O  |O  |O  |O  |   |   |   |   |   |
|macOS El Capitan (64 bits)           |   |O  |O  |O  |   |   |   |   |   |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="see-also"></a>Voir aussi

[Notes de publication](../../connect/php/release-notes-php-sql-driver.md)

[Ressources de support](../../connect/php/support-resources-for-the-php-sql-driver.md)

[Configuration système requise](../../connect/php/system-requirements-for-the-php-sql-driver.md)
