---
title: Architecture de conducteur ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], architecture
ms.assetid: 21a62c7c-192e-4718-a16e-aa12b0de4419
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 712de6a7a3f80ce1cd3ca854a88765dbfa531356
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294557"
---
# <a name="odbc-driver-architecture"></a>Architecture des pilotes ODBC
Les auteurs de pilotes doivent savoir que l’architecture du conducteur peut influer sur la question de savoir si une application peut utiliser SQL spécifique à DBMS.  
  
 ![Présente l'architecture du pilote ODBC](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCDriverOvruArch")  
  
 [Pilotes basés sur des fichiers](../../../odbc/reference/file-based-drivers.md)  
  
 Lorsque le conducteur accède directement aux données physiques, le conducteur agit à la fois comme conducteur et source de données. Le conducteur doit traiter à la fois les appels ODBC et les relevés SQL. Les développeurs de pilotes basés sur des fichiers doivent écrire leurs propres moteurs de base de données.  
  
 [Pilotes basés sur le SGDB](../../../odbc/reference/dbms-based-drivers.md)  
  
 Lorsqu’un moteur de base de données distinct est utilisé pour accéder aux données physiques, le conducteur ne traite que les appels ODBC. Il transmet les relevés SQL au moteur de base de données pour le traitement.  
  
 [Architecture réseau](../../../odbc/reference/network-example.md)  
  
 Les configurations de fichiers et DBMS ODBC peuvent exister sur un seul réseau.  
  
 [Autres architectures de pilote](../../../odbc/reference/other-driver-architectures.md)  
  
 Lorsqu’un conducteur est tenu de travailler avec une variété de sources de données, il peut être utilisé comme middleware. L’architecture hétérogène du moteur de jointure peut faire apparaître le conducteur en tant que gestionnaire de conducteur. Les pilotes peuvent également être installés sur des serveurs, où ils peuvent être partagés par une série de clients.  
  
 Pour plus d’informations sur l’architecture du conducteur, voir [Driver Manager](../../../odbc/reference/the-driver-manager.md) et [Driver Architecture](../../../odbc/reference/driver-architecture.md) dans la section sur [ODBC Architecture](../../../odbc/reference/odbc-architecture.md).  
  
 Vous trouverez de plus amples renseignements sur les problèmes de conduite dans les endroits décrits dans le tableau suivant.  
  
|Problème|Rubrique|Emplacement|  
|-----------|-----------|--------------|  
|Problèmes de compatibilité avec les applications et les conducteurs|[Compatibilité application/conducteur](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Considérations de programmation](../../../odbc/reference/develop-app/programming-considerations.md), dans la référence du programmeur de l’ODBC|  
|Rédaction de pilotes ODBC|[Écriture de pilotes ODBC 3.x](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Considérations de programmation](../../../odbc/reference/develop-app/programming-considerations.md), dans la référence du programmeur de l’ODBC|  
|Lignes directrices du conducteur pour la compatibilité vers l’arrière|[Conseils sur les pilotes pour la compatibilité descendante](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Annexe G: Lignes directrices du conducteur pour la compatibilité rétrograde](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md), dans la référence du programmeur ODBC|  
|Connexion à un conducteur|[Choix d’une source de données ou d’un pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[Connexion à une source de données ou un pilote](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), dans la référence du programmeur ODBC|  
|Identifier les conducteurs|[Affichage des pilotes](../../../odbc/admin/viewing-drivers.md)|[Afficher les pilotes](../../../odbc/admin/viewing-drivers.md), dans l’administrateur Microsoft ODBC Data Source Aide en ligne|  
|Permettre la mise en commun des connexions|[Mise en commun des connexions ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[Connexion à une source de données ou un pilote](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), dans la référence du programmeur ODBC|  
|Problèmes de chauffeur et de connexion Unicode/ANSI|[Pilotes Unicode](../../../odbc/reference/develop-app/unicode-drivers.md)|[Considérations de programmation](../../../odbc/reference/develop-app/programming-considerations.md), dans la référence du programmeur de l’ODBC|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
