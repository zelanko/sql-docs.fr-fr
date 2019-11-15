---
title: Bibliothèque de fonctions R olapR
description: Présentation de la bibliothèque de fonctions olapR dans SQL Server 2016 R Services et SQL Server Machine Learning Services avec R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 507bd04140880a3c15f1e72eed49c29ade56769c
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715005"
---
# <a name="olapr-r-library-in-sql-server"></a>olapR (bibliothèque R dans SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**olapR** est une bibliothèque Microsoft de fonctions R utilisées pour les requêtes MDX sur un cube OLAP SQL Server Analysis Services. Les fonctions ne prennent pas en charge toutes les opérations MDX, mais vous pouvez créer des requêtes qui découpent en tranches, découpent en cubes, descendent dans la hiérarchie, regroupent et pivotent dans plusieurs dimensions. 

Ce package n’est pas préchargé dans une session R. Exécutez la commande suivante pour charger la bibliothèque.

```R
library(olapR)
```

Vous pouvez utiliser cette bibliothèque sur les connexions à un cube OLAP Analysis Services sur toutes les versions de SQL Server prises en charge. Les connexions à un modèle tabulaire ne sont pas prises en charge pour l’instant.

## <a name="package-version"></a>Version du package

Dans tous les produits Windows et dans tous les téléchargements qui incluent la bibliothèque, la version actuelle est 1.0.0.

## <a name="full-reference-documentation"></a>Documentation de référence complète

La bibliothèque **olapr** est distribuée dans plusieurs produits Microsoft, mais l’utilisation est la même que vous obteniez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont les mêmes, la [documentation de chaque fonction sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) est publiée au même endroit sous la [référence R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour Microsoft Machine Learning Server. Si des comportements spécifiques à un produit existent, les différences seront signalées dans la page d’aide de la fonction.

## <a name="availability-and-location"></a>Disponibilité et emplacement

Ce package est fourni dans les produits suivants, ainsi que sur plusieurs images de machine virtuelle sur Azure. L’emplacement du package varie en conséquence.

Product | Emplacement |
--------|----------|
SQL Server Machine Learning Services (avec intégration R) | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R Services | C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R Server) | C:\Program Files\Microsoft\R_SERVER\library |
Microsoft R Client | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Data Science Virtual Machine (sur Azure) | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Machine virtuelle SQL Server (sur Azure) <sup>1</sup> | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> L’intégration R est facultative dans SQL Server. La bibliothèque olapR est installée lorsque vous ajoutez la fonctionnalité Machine Learning ou R au moment de la configuration de la machine virtuelle.


## <a name="see-also"></a>Voir aussi

[Guide pratique pour créer des requêtes MDX à l’aide d’olapR](how-to-create-mdx-queries-using-olapr.md)
