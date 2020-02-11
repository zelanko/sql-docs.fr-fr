---
title: Détermination des SGBD et des pilotes cibles | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7065aa88d60a508df9946d38d0dded220c4bb7a1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106139"
---
# <a name="determining-the-target-dbmss-and-drivers"></a>Détermination des SGBD et des pilotes cibles
La question suivante à prendre en compte est, quels sont les SGBD cibles pour l’application et quels pilotes sont disponibles pour prendre en charge ces SGBD ? Étant donné que les applications génériques ont tendance à être très interopérables, la question des SGBD cibles est la plus applicable aux applications personnalisées et verticales. Toutefois, la question des pilotes cibles s’applique à toutes les applications, car les pilotes varient largement en vitesse, qualité, prise en charge des fonctionnalités et disponibilité. En outre, si les pilotes doivent être redistribués avec l’application, le coût et la disponibilité des plans de licences doivent être pris en compte.  
  
 Pour de nombreuses applications personnalisées, les SGBD cibles sont évidents : il s’agit de SGBD existants auxquels l’application est conçue pour accéder. Les SGBD sur lesquels une migration future est planifiée doivent également être pris en compte. Toutefois, la question majeure de ces applications est le pilote ou les pilotes à utiliser avec eux. Pour les autres applications personnalisées, celles qui ne sont pas conçues pour accéder à un SGBD existant, les SGBD cibles peuvent être choisis en fonction de la prise en charge des fonctionnalités, de la prise en charge simultanée des utilisateurs, de la disponibilité des pilotes et des possibilités d’utilisation.  
  
 Pour les applications verticales, les SGBD cibles sont généralement choisis en fonction de la prise en charge des fonctionnalités, de la disponibilité des pilotes et du marché. Par exemple, une application verticale conçue pour les petites entreprises doit cibler des SGBD qui sont abordables pour ces entreprises. une application verticale conçue comme un module complémentaire pour les SGBD existants doit cibler des SGBD largement utilisés.  
  
 Lorsque vous choisissez des SGBD cibles, les différences entre les bases de données de bureau et de serveur doivent être prises en compte. Les bases de données de bureau telles que dBASE, Paradox et Btrieve sont moins puissantes que les bases de données serveur. Étant donné qu’ils sont généralement accessibles via les moteurs SQL moins puissants qui se trouvent dans la plupart des pilotes basés sur des fichiers, ils n’ont généralement pas de prise en charge complète des transactions, prennent en charge moins d’utilisateurs simultanés et ont un SQL limité. Toutefois, elles sont peu coûteuses et ont une base installée volumineuse.  
  
 Les bases de données de serveur telles qu’Oracle, DB2 et SQL Server fournissent une prise en charge complète des transactions, prennent en charge de nombreux utilisateurs simultanés et ont des fonctionnalités SQL enrichies. Elles sont beaucoup plus coûteuses et ont une base installée plus petite. En revanche, les prix des logiciels ont tendance à être plus élevés, ce qui compense un marché potentiel plus petit.  
  
 Ainsi, les SGBD cibles peuvent parfois être choisis en fonction des fonctionnalités requises par l’application et du marché cible de l’application. Par exemple, un système de saisie des commandes pour les grandes entreprises peut ne pas cibler les bases de données de bureau, car celles-ci ne prennent pas en charge les transactions. Un système similaire conçu pour les petites entreprises peut exclure la plupart des bases de données de serveur en fonction du coût. Et les développeurs d’applications génériques peuvent cibler les deux, mais évitez d’utiliser les fonctionnalités avancées disponibles dans les bases de données serveur.
