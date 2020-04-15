---
title: À propos des conducteurs et des sources de données ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7dffeea3bea7e3fbfa66e534ecaa758fbc2064d5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307220"
---
# <a name="about-drivers-and-data-sources"></a>À propos des pilotes et des sources de données
*Les conducteurs* sont les composants qui traitent les demandes d’ODBC et retournent les données à l’application. Si nécessaire, les conducteurs modifient la demande d’une application sous un formulaire qui est compris par la source de données. Vous devez utiliser le programme d’installation du pilote pour ajouter ou supprimer un pilote de votre ordinateur.  
  
 *Les sources de données* sont les bases de données ou les fichiers consultés par un conducteur et sont identifiés par un nom de source de données (DSN). Utilisez l’administrateur de source de données ODBC pour ajouter, configurer et supprimer les sources de données de votre système. Les types de sources de données qui peuvent être utilisées sont décrits dans le tableau suivant.  
  
|Source de données|Description|  
|-----------------|-----------------|  
|Utilisateur|Les DSN utilisateurs sont locaux à un ordinateur et ne peuvent être utilisés que par l’utilisateur actuel. Ils sont enregistrés dans le sous-HKEY_CURRENT_USER registre.|  
|Système|Les DSN système sont locaux à un ordinateur plutôt que dédiés à un utilisateur. Le système ou tout utilisateur ayant des privilèges peut utiliser une source de données configuré avec un système DSN. Les DSN système sont enregistrés dans le sous-ensemble de registre HKEY_LOCAL_MACHINE.|  
|Fichier|Les DSN de fichiers sont des sources basées sur des fichiers qui peuvent être partagées entre tous les utilisateurs qui ont les mêmes pilotes installés et ont donc accès à la base de données. Ces sources de données n’ont pas besoin d’être dédiées à un utilisateur ni d’être locales à un ordinateur. Les noms des sources de données de fichiers ne sont pas identifiés par les entrées de registre dédiées; au lieu de cela, ils sont identifiés par un nom de fichier avec une extension .dsn.|  
  
 Les sources de données des utilisateurs et du système sont collectivement connues sous le nom de sources de données *de machine* parce qu’elles sont locales à un ordinateur.  
  
 Chacune de ces sources de données a un onglet dans la boîte de dialogue **ODBC Data Source Administrator.** Pour plus d’informations sur les sources de données disponibles, consultez [Sources de données](../../odbc/reference/data-sources.md).
