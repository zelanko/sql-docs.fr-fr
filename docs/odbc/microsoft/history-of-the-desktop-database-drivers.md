---
title: Historique des pilotes de base de données de bureau | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], history
- ODBC desktop database drivers [ODBC], history
- desktop database drivers [ODBC], history
ms.assetid: b4a2aff8-bde7-4bd5-8580-bc50f27311c8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a77aeafff6b27b2de0b947700cef1c7251cd7548
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63127267"
---
# <a name="history-of-the-desktop-database-drivers"></a>Historique des pilotes pour les bases de données de poste de travail
Le tableau suivant présente l’historique des versions de pilotes de base de données de bureau.  
  
|Version|Date de sortie|Description|  
|-------------|------------------|-----------------|  
|1.0|Août 1993|Utilisé le processeur de requêtes SIMBA produit par les logiciels PageAhead. SIMBA reçu des appels ODBC et des instructions SQL, le traitement en appels ISAM installables de Microsoft Jet et ensuite appelée la couche de distribution Microsoft Jet ISAM pour charger et appeler le pilote ISAM installable approprié.|  
|2|Décembre 1994|Utilisée avec ODBC 2.0, qui a considérablement augmenté la fonctionnalité ODBC. Le changement majeur dans la version 2.0 a été que le moteur de base de données Microsoft Jet remplacé le processeur de requêtes SIMBA. Avec le moteur de base de données Microsoft Jet, les pilotes de base de données de bureau intégré beaucoup plus étroitement avec les pilotes ISAM installables de Microsoft Jet et la technologie de Microsoft Access. Des améliorations significatives ont été :<br /><br /> -Prise en charge native des curseurs avec défilement.<br />-Prise en charge native jointures externes, les jointures hétérogènes et mettre à jour et les transactions.<br />-les versions 32 bits des pilotes pour Microsoft Windows NT.|  
|3|Octobre 1995|Fourni la prise en charge de Windows 95 et Windows NT Workstation ou Server NT 3.51. Seuls les pilotes 32 bits ont été inclus dans cette version. les pilotes 16 bits pour Windows version 3.1 ont été supprimés.|  
|3.5|Octobre 1996|Ces pilotes ont été le jeu de caractères de deux octets (DBCS)-activée, ont été mieux adaptée pour une utilisation avec les applications Internet que les versions antérieures et prise en charge l’utilisation de noms de source de données de fichier (DSN). Le pilote Microsoft Access a été publié dans une version RISC pour une utilisation sur les plates-formes Alpha pour Windows 95/98 et Windows NT 3.51 et systèmes d’exploitation ultérieurs.|  
|4.0|Liaison tardive 1998|Prend en charge du format Unicode moteur Jet de Microsoft, ainsi que de compatibilité pour le format ANSI des versions antérieures.|  
  
> [!NOTE]  
>  Les pilotes version3.5 ont été conçus pour fonctionner avec ODBC2. *x*. Bien qu’ils fonctionnent également avec ODBC 3.0, ils ne gèrent pas toutes les fonctions ODBC 3.0. Pour plus d’informations sur le fonctionnement de ces pilotes avec ODBC 3.0, consultez [la compatibilité descendante et conformité aux normes](../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).
