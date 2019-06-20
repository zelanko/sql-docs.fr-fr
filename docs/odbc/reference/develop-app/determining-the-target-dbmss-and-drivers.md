---
title: Détermination de la cible SGBD et des pilotes | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 92da788205213394edc75257d8266752a2a9d8df
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63034946"
---
# <a name="determining-the-target-dbmss-and-drivers"></a>Détermination des SGBD et des pilotes cibles
La question suivante à prendre en compte est, quelles sont le SGBD cible pour l’application, et quels pilotes sont disponibles qui prennent en charge ces SGBD ? Étant donné que les applications génériques ont tendance à être hautement interopérable, la question de cible de SGBD est plus applicable aux applications personnalisées et verticales. Toutefois, la question des pilotes cibles s’applique à toutes les applications, étant donné que les pilotes peuvent varier en vitesse, qualité, prise en charge de fonctionnalité et de disponibilité. En outre, si les pilotes doivent être redistribué avec l’application, le coût et la disponibilité des plans de licence faut tenir compte.  
  
 Pour de nombreuses applications personnalisées, la cible du SGBD sont évidents : Ils sont des SGBD l’application est conçue pour y accéder. SGBD auquel est prévue future migration doit également être considérée. Toutefois, la question majeure pour ces applications est l’ou les pilotes à utiliser avec eux. Pour d’autres applications personnalisées : celles qui ne sont pas conçus pour accéder à un SGBD existant - la SGBD cible peut être choisie en fonction de prise en charge de la fonctionnalité, prise en charge des utilisateurs simultanés, disponibilité du pilote et prix abordable.  
  
 Pour applications verticales, la cible de que SGBD est généralement choisi dépend de prise en charge de la fonctionnalité, la disponibilité du pilote et sur le marché. Par exemple, une application verticale conçue pour les petites entreprises doit cibler les SGBD qui s’adaptent à ces entreprises. une application verticale conçue comme un module complémentaire pour les SGBD existants doit cibler largement utilisé SGBD.  
  
 Lorsque vous choisissez cible SGBD, les différences entre les bureaux et serveurs de bases de données doivent être envisagés. Bases de données bureautiques, dBASE, Paradox et Btrieve sont moins puissants que les bases de données de serveur. Car ils sont généralement accessibles via les moins puissants moteurs SQL trouvées dans les pilotes plus basé sur fichier, souvent, ils ne disposent pas de prise en charge des transactions saturé, prennent en charge un nombre d’utilisateurs simultanés et sont limitée à SQL. Cependant, ils sont onéreux et ont une grande base installée.  
  
 Bases de données de serveur telles que Oracle, DB2 et SQL Server prennent en charge complète des transactions prend en charge de nombreux utilisateurs simultanés et ont SQL riche. Ils sont beaucoup plus onéreux et ont une plus petite base installée. Quant à eux, les prix de logiciels ont tendance à être plus élevé, quelque peu compensation un marché potentiel plus petits.  
  
 Par conséquent, vous pouvez choisir cible SGBD parfois selon les fonctionnalités requises par l’application et sur le marché de l’application cible. Par exemple, un système de saisie de commandes pour les grandes entreprises peuvent ne pas cible des bases de données bureautiques, car ils ne disposent pas de prise en charge de transaction adéquat. Un système semblable conçu pour les petites entreprises peut-être exclure la plupart des bases de données de serveur sur la base de coût. Et les développeurs d’applications génériques peuvent cibler à la fois mais évitez d’utiliser les fonctionnalités avancées de bases de données de serveur.
