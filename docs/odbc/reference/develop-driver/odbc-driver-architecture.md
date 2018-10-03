---
title: Architecture du pilote ODBC | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 260767c88fdf980466a21d4cc9658b259b91c854
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788147"
---
# <a name="odbc-driver-architecture"></a>Architecture des pilotes ODBC
Les rédacteurs de pilotes doivent être conscients que l’architecture du pilote peut affecter si une application peut utiliser SQL de SGBD spécifiques.  
  
 ![Montre l’architecture du pilote ODBC](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCDriverOvruArch")  
  
 [Pilotes basés sur un fichier](../../../odbc/reference/file-based-drivers.md)  
  
 Lorsque le pilote accède directement aux données physiques, le pilote joue le rôle de source de données et que les pilotes. Le pilote doit traiter des appels ODBC et les instructions SQL. Les développeurs de pilotes basés sur le fichier doivent écrire leurs propres moteurs de base de données.  
  
 [Pilotes basés sur le SGDB](../../../odbc/reference/dbms-based-drivers.md)  
  
 En cas d’un moteur de base de données distincte est utilisé pour accéder aux données physiques, le pilote traite uniquement les appels ODBC. Il passe les instructions SQL au moteur de base de données pour traitement.  
  
 [Architecture réseau](../../../odbc/reference/network-example.md)  
  
 Les configurations de fichiers et DBMS ODBC peuvent exister sur un réseau unique.  
  
 [Autres architectures de pilote](../../../odbc/reference/other-driver-architectures.md)  
  
 Lorsqu’un pilote est requis pour fonctionner avec un large éventail de sources de données, il peut être utilisé comme intergiciel (middleware). Architecture du moteur de jointure hétérogène peut rendre le pilote apparaissent sous la forme d’un gestionnaire de pilotes. Pilotes peuvent également être installés sur les serveurs, où ils peuvent être partagés par une série de clients.  
  
 Pour plus d’informations sur l’architecture du pilote, consultez [Gestionnaire de pilotes](../../../odbc/reference/the-driver-manager.md) et [Architecture du pilote](../../../odbc/reference/driver-architecture.md) dans la section sur [Architecture ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Vous trouverez plus d’informations sur les problèmes liés aux pilotes dans les emplacements décrits dans le tableau suivant.  
  
|Problème|Rubrique|Emplacement|  
|-----------|-----------|--------------|  
|Problèmes de compatibilité avec les applications et les pilotes|[Compatibilité d’application/pilote](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Considérations sur la programmation](../../../odbc/reference/develop-app/programming-considerations.md), dans la référence du programmeur ODBC|  
|Pilotes ODBC de rédaction|[Écriture de pilotes ODBC 3.x](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Considérations sur la programmation](../../../odbc/reference/develop-app/programming-considerations.md), dans la référence du programmeur ODBC|  
|Conseils sur les pilotes pour la compatibilité descendante|[Conseils sur les pilotes pour la compatibilité descendante](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Annexe g : conseils sur les pilotes pour la compatibilité descendante](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md), dans la référence du programmeur ODBC|  
|Connexion à un pilote|[Choix d’une source de données ou d’un pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[Connexion à une données Source ou le pilote](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), dans la référence du programmeur ODBC|  
|Identification des pilotes|[Affichage des pilotes](../../../odbc/admin/viewing-drivers.md)|[Affichage des pilotes](../../../odbc/admin/viewing-drivers.md), l’administrateur de sources de données ODBC Microsoft aide en ligne|  
|Activer le regroupement de connexions|[Le regroupement de connexions ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[Connexion à une données Source ou le pilote](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), dans la référence du programmeur ODBC|  
|Problèmes de pilote et de connexion Unicode/ANSI|[Pilotes Unicode](../../../odbc/reference/develop-app/unicode-drivers.md)|[Considérations sur la programmation](../../../odbc/reference/develop-app/programming-considerations.md), dans la référence du programmeur ODBC|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
