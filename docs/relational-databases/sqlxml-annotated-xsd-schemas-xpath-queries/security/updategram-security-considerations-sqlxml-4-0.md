---
title: Considérations relatives à la sécurité mise à jour (SQLXML)
description: Découvrez les instructions de sécurité pour l’utilisation de codes dans SQLXML 4,0.
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- security [SQLXML], updategrams
- updategrams [SQLXML], security
ms.assetid: 00dc6cf4-a2e8-4cca-bdd6-d5122102a82d
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 23214cd1120061f6da9c6df46f08fd1c7a0df04a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97479230"
---
# <a name="updategram-security-considerations-sqlxml-40"></a>Considérations de sécurité relatives au code de mise à jour (updategram) (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Vous trouverez ci-après des instructions de sécurité relatives à l'utilisation des codes de mise à jour :  
  
-   Évitez d'utiliser le mappage par défaut lorsque vous utilisez des codes de mise à jour pour mettre à jour des données. Lorsque vous utilisez le mappage par défaut, un nom d'élément dans un code de mise à jour mappe à un nom de table et un nom d'attribut mappe à une colonne. Cela expose les informations de colonnes et de tables dans la base de données, ce qui constitue un problème de sécurité potentiel. Au lieu de cela, si vous spécifiez un schéma de mappage séparé qui mappe les éléments et attributs dans un code de mise à jour aux tables et colonnes de base de données, vos noms d'attributs et d'éléments de code de mise à jour peuvent être arbitraires et le schéma effectue un mappage nécessaire de ces noms aux tables et colonnes de base de données. Ainsi, les informations sur la base de données ne sont pas exposées dans un code de mise à jour.  
  
-   N'autorisez pas les utilisateurs à créer et exécuter leurs codes de mise à jour. Il est recommandé de faire en sorte que les codes de mise à jour résident en tant que modèles sur un serveur, plutôt que les créer de manière dynamique dans des applications de type ASP, ce qui pourraient exposer les données de la base de données. Le fait d'autoriser les utilisateurs à accéder uniquement aux données par le biais des codes de mise à jour fournis en tant que modèles peut éliminer ce risque.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de codes de mise à jour (updategrams) pour modifier des données dans SQLXML 4.0](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
  
  
