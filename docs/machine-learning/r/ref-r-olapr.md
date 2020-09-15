---
title: Package R olapR
description: olapR est un package R de Microsoft servant à effectuer des requêtes MDX sur un cube OLAP SQL Server Analysis Services. Les fonctions ne prennent pas en charge toutes les opérations MDX, mais vous pouvez créer des requêtes qui découpent en tranches, découpent en cubes, descendent dans la hiérarchie, regroupent et pivotent dans plusieurs dimensions. Il est inclus dans SQL Server Machine Learning Services et dans SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/14/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ba5f9677022eb07a8810f3ea9c5dcffeaa716e7c
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88179924"
---
# <a name="olapr-r-package-in-sql-server-machine-learning-services"></a>olapR (package R de SQL Server Machine Learning Services)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

**olapR** est un package R de Microsoft servant à effectuer des requêtes MDX sur un cube OLAP SQL Server Analysis Services. Les fonctions ne prennent pas en charge toutes les opérations MDX, mais vous pouvez créer des requêtes qui découpent en tranches, découpent en cubes, descendent dans la hiérarchie, regroupent et pivotent dans plusieurs dimensions. Il est inclus dans [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) et dans [SQL Server 2016 R Services](sql-server-r-services.md).

Vous pouvez utiliser ce package sur les connexions à un cube OLAP Analysis Services sur toutes les versions de SQL Server prises en charge. Les connexions à un modèle tabulaire ne sont pas prises en charge pour l’instant.

## <a name="load-package"></a>Chargement du package

Le package **olapR** n’est pas préchargé dans une session R. Exécutez la commande suivante pour le charger.

```R
library(olapR)
```

## <a name="package-version"></a>Version du package

La version actuelle est 1.0.0 dans tous les téléchargements et produits Windows uniquement qui fournissent le package.

## <a name="full-reference-documentation"></a>Documentation de référence complète

Le package **olapR** est distribué dans plusieurs produits Microsoft, mais l’utilisation est la même quelle que soit sa provenance (SQL Server ou un autre produit). Étant donné que les fonctions sont les mêmes, la [documentation de chaque fonction sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) est publiée au même endroit sous la [référence R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour Microsoft Machine Learning Server. Si des comportements spécifiques à un produit existent, les différences seront signalées dans la page d’aide de la fonction.

## <a name="availability-and-location"></a>Disponibilité et emplacement

Ce package est fourni dans les produits suivants, ainsi que sur plusieurs images de machine virtuelle sur Azure. L’emplacement du package varie en conséquence.

Produit | Emplacement |
--------|----------|
SQL Server Machine Learning Services (avec intégration R) | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R Services | C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R Server) | C:\Program Files\Microsoft\R_SERVER\library |
Microsoft R Client | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Data Science Virtual Machine (sur Azure) | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Machine virtuelle SQL Server (sur Azure) <sup>1</sup> | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> L’intégration R est facultative dans SQL Server. Le package olapR est installé lorsque la fonctionnalité Machine Learning ou R est ajoutée au moment de la configuration de la machine virtuelle.


## <a name="see-also"></a>Voir aussi

[Guide pratique pour créer des requêtes MDX à l’aide d’olapR](how-to-create-mdx-queries-using-olapr.md)
