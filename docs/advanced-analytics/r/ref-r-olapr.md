---
title: bibliothèque de fonctions olapR R - Services de SQL Server Machine Learning
description: Introduction à la bibliothèque de fonctions olapR dans SQL Server 2016 R Services et SQL Server 2017 Machine Learning Services avec R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e5419900b8ba573ec0658a5022be68105b0b8607
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641856"
---
# <a name="olapr-r-library-in-sql-server"></a>olapR (bibliothèque R dans SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**olapR** est une bibliothèque Microsoft de fonctions R utilisé pour les requêtes MDX sur un cube OLAP de SQL Server Analysis Services. Fonctions ne prennent pas en charge toutes les opérations MDX, mais vous pouvez générer des requêtes que la tranche, découpez en cubes, exploration vers le bas, rollup et sur les dimensions de tableau croisé dynamique. 

Ce package n’est pas préchargé dans une session R. Exécutez la commande suivante pour charger la bibliothèque.

```R
library(olapR)
```

Vous pouvez utiliser cette bibliothèque sur des connexions à un cube OLAP d’Analysis Services sur toutes les versions prises en charge de SQL Server. Connexions à un modèle tabulaire ne sont pas prises en charge pour l’instant.

## <a name="package-version"></a>Version du package

Version actuelle est 1.0.0 dans tous les produits Windows uniquement et télécharge en fournissant la bibliothèque.

## <a name="full-reference-documentation"></a>Documentation de référence complète

Le **olapr** library est distribué dans plusieurs produits Microsoft, mais l’utilisation est la même, si vous obtenez la bibliothèque dans SQL Server ou un autre produit. Étant donné que les fonctions sont les mêmes, [documentation pour les fonctions individuelles sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) est publié dans un seul emplacement sous la [référence de R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) pour Microsoft Machine Learning Server. Doivent tout propres au produit comportements existent, les différences sont notées dans la page d’aide (fonction).

## <a name="availability-and-location"></a>Disponibilité et l’emplacement

Ce package est fourni dans les produits suivants, ainsi que sur plusieurs images de machines virtuelles sur Azure. Emplacement du package varie en conséquence.

Produit | Location |
--------|----------|
SQL Server 2017 Machine Learning Services (avec l’intégration de R) | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R Services | C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R Server) | C:\Program Files\Microsoft\R_SERVER\library |
Microsoft R Client | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Machine virtuelle de science des données (sur Azure) | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Machine virtuelle SQL Server (sur Azure) <sup>1</sup> | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> intégration de R est facultative dans SQL Server. La bibliothèque olapR sera installée lorsque vous ajoutez l’apprentissage ou la fonctionnalité R lors de la configuration de la machine virtuelle.


## <a name="see-also"></a>Voir aussi

[Comment créer des requêtes MDX à l’aide d’olapR](how-to-create-mdx-queries-using-olapr.md)
