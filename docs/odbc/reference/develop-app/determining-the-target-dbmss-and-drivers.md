---
title: Détermination des DBMS et des pilotes cibles . Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- target DBMSs and drivers in interoperability [ODBC]
- interoperability [ODBC], target dbmss and drivers
ms.assetid: 23bee0f6-e12a-4598-b34e-df11a8086829
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f8811e4d289a8fc89c2c3773aab973df523025f5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305870"
---
# <a name="determining-the-target-dbmss-and-drivers"></a>Détermination des SGBD et des pilotes cibles
La prochaine question à considérer est la suivante : quels sont les DBMS cibles pour l’application et quels sont les conducteurs disponibles qui prennent en charge ces DBMS? Étant donné que les applications génériques ont tendance à être hautement interopérables, la question des DBMS cibles s’applique le plus aux applications personnalisées et verticales. Cependant, la question des pilotes cibles s’applique à toutes les applications, car les conducteurs varient considérablement en vitesse, qualité, support de fonctionnalités et disponibilité. De plus, si l’on veut redistribuer les conducteurs avec la demande, le coût et la disponibilité des régimes de délivrance de permis doivent être pris en considération.  
  
 Pour de nombreuses applications personnalisées, les DBMS cibles sont évidentes : il s’agit de DBMS existants auxquels l’application est conçue pour y accéder. Les DBMS auxquels la migration future est prévue devraient également être envisagées. Cependant, la principale question pour ces applications est de savoir quel conducteur ou les conducteurs utiliser avec eux. Pour d’autres applications personnalisées - celles qui ne sont pas conçues pour accéder à un DBMS existant - les DBMS cibles peuvent être choisies en fonction du support des fonctionnalités, du soutien simultané des utilisateurs, de la disponibilité du conducteur et de l’abordabilité.  
  
 Pour les applications verticales, les DBMS cibles sont généralement choisies en fonction du support des fonctionnalités, de la disponibilité du conducteur et du marché. Par exemple, une application verticale conçue pour les petites entreprises doit cibler les DBMS qui sont abordables pour ces entreprises; une application verticale conçue comme un add-on aux DBMS existants doit cibler les DBMS largement utilisés.  
  
 Lors du choix des DBMS cibles, les différences entre les bases de données de bureau et de serveur doivent être prises en considération. Les bases de données de bureau telles que dBASE, Paradox et Btrieve sont moins puissantes que les bases de données de serveurs. Étant donné qu’ils sont généralement accessibles par l’intermédiaire des moteurs SQL moins puissants que l’on trouve dans la plupart des pilotes basés sur des fichiers, ils manquent souvent d’un soutien complet aux transactions, prennent en charge moins d’utilisateurs simultanés et ont un SQL limité. Cependant, ils sont peu coûteux et ont une grande base installée.  
  
 Les bases de données de serveurs telles qu’Oracle, DB2 et SQL Server fournissent un support complet des transactions, prennent en charge de nombreux utilisateurs simultanés et ont un SQL riche. Ils sont beaucoup plus chers et ont une base installée plus petite. D’autre part, les prix des logiciels ont tendance à être plus élevés, ce qui compense quelque peu un marché potentiel plus petit.  
  
 Ainsi, les DBMS cibles peuvent parfois être choisies en fonction des caractéristiques requises par l’application et du marché cible de l’application. Par exemple, un système de saisie de commandes pour les grandes entreprises peut ne pas cibler les bases de données de bureau parce qu’elles manquent d’un soutien adéquat aux transactions. Un système similaire conçu pour les petites entreprises peut exclure la plupart des bases de données de serveurs sur la base du coût. Et les développeurs d’applications génériques peuvent cibler les deux, mais éviter d’utiliser les fonctionnalités avancées trouvées dans les bases de données des serveurs.
