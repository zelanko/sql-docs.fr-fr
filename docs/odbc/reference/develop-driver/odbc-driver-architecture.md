---
description: Architecture des pilotes ODBC
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1789d5799ed9eb15ace7ea263d1a5804c8e86e74
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476245"
---
# <a name="odbc-driver-architecture"></a>Architecture des pilotes ODBC
Les rédacteurs de pilotes doivent savoir que l’architecture du pilote peut déterminer si une application peut utiliser SQL spécifique au SGBD.  
  
 ![Présente l'architecture du pilote ODBC](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCDriverOvruArch")  
  
 [Pilotes basés sur des fichiers](../../../odbc/reference/file-based-drivers.md)  
  
 Lorsque le pilote accède directement aux données physiques, le pilote fait office de source de données et de pilote. Le pilote doit traiter à la fois les appels ODBC et les instructions SQL. Les développeurs de pilotes basés sur des fichiers doivent écrire leurs propres moteurs de base de données.  
  
 [Pilotes basés sur le SGDB](../../../odbc/reference/dbms-based-drivers.md)  
  
 Lorsqu’un moteur de base de données distinct est utilisé pour accéder aux données physiques, le pilote traite uniquement les appels ODBC. Il transmet des instructions SQL au moteur de base de données pour le traitement.  
  
 [Architecture réseau](../../../odbc/reference/network-example.md)  
  
 Les configurations ODBC de fichier et SGBD peuvent exister sur un seul réseau.  
  
 [Autres architectures de pilote](../../../odbc/reference/other-driver-architectures.md)  
  
 Lorsqu’un pilote est requis pour fonctionner avec diverses sources de données, il peut être utilisé comme middleware. L’architecture d’un moteur de jointure hétérogène peut faire apparaître le pilote comme un gestionnaire de pilotes. Les pilotes peuvent également être installés sur des serveurs, où ils peuvent être partagés par une série de clients.  
  
 Pour plus d’informations sur l’architecture des pilotes, consultez [Gestionnaire de pilotes](../../../odbc/reference/the-driver-manager.md) et [architecture de pilote](../../../odbc/reference/driver-architecture.md) dans la section relative à l' [architecture ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Vous trouverez plus d’informations sur les problèmes de pilote dans les emplacements décrits dans le tableau suivant.  
  
|Problème|Rubrique|Emplacement|  
|-----------|-----------|--------------|  
|Problèmes de compatibilité avec les applications et les pilotes|[Compatibilité de l’application/du pilote](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Considérations relatives](../../../odbc/reference/develop-app/programming-considerations.md)à la programmation, dans le Guide de référence du PROGRAMMEur ODBC|  
|Écriture de pilotes ODBC|[Écriture de pilotes ODBC 3.x](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Considérations relatives](../../../odbc/reference/develop-app/programming-considerations.md)à la programmation, dans le Guide de référence du PROGRAMMEur ODBC|  
|Instructions relatives aux pilotes pour la compatibilité descendante|[Conseils sur les pilotes pour la compatibilité descendante](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Annexe G : instructions relatives aux pilotes pour la compatibilité descendante](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md), dans le Guide de référence du PROGRAMMEur ODBC|  
|Connexion à un pilote|[Choix d’une source de données ou d’un pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[Connexion à une source de données ou à un pilote](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), dans le Guide de référence du PROGRAMMEur ODBC|  
|Identification des pilotes|[Affichage des pilotes](../../../odbc/admin/viewing-drivers.md)|[Affichage des pilotes](../../../odbc/admin/viewing-drivers.md), dans l’aide en ligne de l’administrateur de la source de données Microsoft ODBC|  
|Activation du regroupement de connexions|[Regroupement de connexions ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[Connexion à une source de données ou à un pilote](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), dans le Guide de référence du PROGRAMMEur ODBC|  
|Problèmes de connexion et de pilote Unicode/ANSI|[Pilotes Unicode](../../../odbc/reference/develop-app/unicode-drivers.md)|[Considérations relatives](../../../odbc/reference/develop-app/programming-considerations.md)à la programmation, dans le Guide de référence du PROGRAMMEur ODBC|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
