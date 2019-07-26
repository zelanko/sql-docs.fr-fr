---
title: bibliothèque de fonctions OLAP R
description: Présentation de la bibliothèque de fonctions OLAP dans SQL Server 2016 R services et SQL Server 2017 Machine Learning Services avec R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 674e4ed4d1967452093e81e7bb4f5518d9237cf6
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469979"
---
# <a name="olapr-r-library-in-sql-server"></a>olapr (bibliothèque R dans SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**olapr** est une bibliothèque Microsoft de fonctions R utilisées pour les requêtes MDX sur un cube SQL Server Analysis Services OLAP. Les fonctions ne prennent pas en charge toutes les opérations MDX, mais vous pouvez créer des requêtes qui découpent les dimensions, les dés, les descente, les cumuls et les tableaux croisés dynamiques. 

Ce package n’est pas préchargé dans une session R. Exécutez la commande suivante pour charger la bibliothèque.

```R
library(olapR)
```

Vous pouvez utiliser cette bibliothèque sur les connexions à un cube Analysis Services OLAP sur toutes les versions de SQL Server prises en charge. Les connexions à un modèle tabulaire ne sont pas prises en charge pour l’instant.

## <a name="package-version"></a>Version du package

La version actuelle est 1.0.0 dans tous les produits Windows et les téléchargements qui fournissent la bibliothèque.

## <a name="full-reference-documentation"></a>Documentation de référence complète

La  bibliothèque olapr est distribuée dans plusieurs produits Microsoft, mais l’utilisation est la même que vous obteniez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont identiques, la [documentation des fonctions sqlrutils individuelles](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) est publiée dans un seul emplacement sous la [référence R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour Microsoft machine learning Server. Si des comportements spécifiques à un produit existent, les différences seront signalées dans la page d’aide de la fonction.

## <a name="availability-and-location"></a>Disponibilité et emplacement

Ce package est fourni dans les produits suivants, ainsi que sur plusieurs images de machine virtuelle sur Azure. L’emplacement du package varie en conséquence.

Produit | Location |
--------|----------|
SQL Server 2017 Machine Learning Services (avec intégration R) | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R services | C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R Server) | C:\Program Files\Microsoft\R_SERVER\library |
Microsoft R Client | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Data Science Virtual Machine (sur Azure) | C:\Program Files\Microsoft\R Client\R_SERVER\library |
SQL Server de la machine virtuelle (sur Azure) <sup>1</sup> | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> l’intégration R est facultative dans SQL Server. La bibliothèque olapr est installée lorsque vous ajoutez la fonctionnalité Machine Learning ou R lors de la configuration de l’ordinateur virtuel.


## <a name="see-also"></a>Voir aussi

[Comment créer des requêtes MDX à l’aide d’olapr](how-to-create-mdx-queries-using-olapr.md)
