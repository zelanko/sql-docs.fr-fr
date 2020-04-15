---
title: Historique des pilotes de base de données de bureau (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89434b397c07fdee751ca4272b65ac2eada94cf3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304980"
---
# <a name="history-of-the-desktop-database-drivers"></a>Historique des pilotes pour les bases de données de poste de travail
Le tableau suivant affiche l’historique de la version Desktop Database Drivers.  
  
|Version|Date de sortie|Description|  
|-------------|------------------|-----------------|  
|1.0|En août 1993|Utilisé le processeur de requête SIMBA produit par PageAhead Software. SIMBA a reçu des appels ODBC et des déclarations SQL, les a traitées en appels ISAM installables Microsoft Jet, puis a appelé la couche de répartition Microsoft Jet ISAM pour charger et appeler le pilote ISAM installable approprié.|  
|2|En décembre 1994|Utilisé avec ODBC 2.0, qui a considérablement élargi la fonctionnalité ODBC. Le principal changement dans la version 2.0 était que le moteur de base de données Microsoft Jet a remplacé le processeur de requête SIMBA. Avec le moteur de base de données Microsoft Jet, les desktop Database Drivers se sont intégrés beaucoup plus étroitement avec les pilotes ISAM installables Microsoft Jet et la technologie Microsoft Access. Les améliorations importantes ont été les :<br /><br /> - Soutien autochtone pour les curseurs défilementables.<br />- Soutien autochtone pour les jointures extérieures, les jointures updatables et hétérogènes, et les transactions.<br />- Versions 32 bits des pilotes de Microsoft Windows NT.|  
|3.0|En octobre 1995|A fourni une prise en charge pour Windows 95 et Windows NT Workstation ou NT Server 3.51. Seuls les conducteurs 32 bits ont été inclus dans cette version; les pilotes 16 bits pour la version Windows 3.1 ont été supprimés.|  
|3,5|En octobre 1996|Ces pilotes étaient compatibles avec des caractères doubles par tant etins (DBCS), étaient mieux adaptés aux applications Internet que les versions précédentes et s’adaptaient à l’utilisation des noms de source de données de fichiers (DSN). Le pilote Microsoft Access a été publié dans une version RISC pour une utilisation sur les plates-formes Alpha pour Windows 95/98 et Windows NT 3.51 et plus tard les systèmes d’exploitation.|  
|4.0|Fin 1998|Fournit un support pour le format Microsoft Jet Engine Unicode ainsi que la compatibilité pour le format ANSI des versions antérieures.|  
  
> [!NOTE]  
>  Les pilotes version3.5 ont été conçus pour travailler avec ODBC2. *x*. Bien qu’ils travaillent également avec ODBC 3.0, ils ne prennent pas en charge toutes les fonctionnalités ODBC 3.0. Pour plus d’informations sur la façon dont ces conducteurs travaillent avec ODBC 3.0, voir [Rétrospectibilité et conformité aux normes](../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).
