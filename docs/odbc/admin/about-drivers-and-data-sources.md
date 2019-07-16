---
title: Sur les pilotes et les Sources de données | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4e9b7229882b3b7f94e6b059e04c6496bde09641
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938040"
---
# <a name="about-drivers-and-data-sources"></a>À propos des pilotes et des sources de données
*Pilotes* sont les composants qui traitent les demandes d’ODBC et retournent des données à l’application. Si nécessaire, pilotes de modifier la requête d’une application dans un formulaire qui est interprété par la source de données. Vous devez utiliser le programme d’installation du pilote pour ajouter ou supprimer un pilote à partir de votre ordinateur.  
  
 *Sources de données* sont les bases de données ou les fichiers accédés par un pilote et sont identifiés par un nom de source de données (DSN). Utilisez l’administrateur de sources de données ODBC pour ajouter, configurer et supprimer des sources de données de votre système. Les types de sources de données qui peuvent être utilisés sont décrits dans le tableau suivant.  
  
|Source de données|Description|  
|-----------------|-----------------|  
|Utilisateur|Sources de données utilisateur locales sur un ordinateur et peuvent être utilisées uniquement par l’utilisateur actuel. Ils sont inscrits dans la sous-arborescence de Registre HKEY_CURRENT_USER.|  
|System|Sources de données système sont locales à un ordinateur plutôt que dédié à un utilisateur. Le système ou n’importe quel utilisateur disposant de privilèges peut utiliser une source de données configurée avec un DSN système. Sources de données système sont enregistrés dans la sous-arborescence de Registre HKEY_LOCAL_MACHINE.|  
|Fichier|Sources de données fichier sont des sources de fichier qui peuvent être partagées entre tous les utilisateurs qui ont les mêmes pilotes installés et par conséquent ont accès à la base de données. Ces sources de données ne doivent pas être dédiées à un utilisateur, ni se trouver sur un ordinateur. Noms de source de données de fichiers ne sont pas identifiées par les entrées de Registre dédié ; au lieu de cela, ils sont identifiés par un nom de fichier avec une extension .dsn.|  
  
 Sources de données utilisateur et système sont collectivement regroupés sous *machine* sources de données, car elles sont locales à un ordinateur.  
  
 Chacune de ces sources de données dispose d’un onglet le **administrateur de sources de données ODBC** boîte de dialogue. Pour plus d’informations sur les sources de données disponibles, consultez [Sources de données](../../odbc/reference/data-sources.md).
