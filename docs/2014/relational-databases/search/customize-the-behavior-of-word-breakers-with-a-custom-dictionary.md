---
title: Personnaliser le comportement des analyseurs lexicaux avec un dictionnaire personnalisé | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
caps.latest.revision: 5
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 57a31544150f34d3f8d48c419bb91d4f9622c225
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045124"
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>Personnaliser le comportement des analyseurs lexicaux avec un dictionnaire personnalisé
  Vous pouvez personnaliser le comportement de l'analyseur lexical pour une langue particulière en créant un fichier de dictionnaire personnalisé propre à une langue. Par exemple, vous pouvez empêcher l'analyseur lexical de séparer certains termes ou modèles.  
  
 Pour plus d'informations, consultez l'article SharePoint suivant :  
  
 [Créer un dictionnaire personnalisé (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=215011)  
  
 Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], placez les fichiers de dictionnaire personnalisés dans le dossier suivant :  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 Après avoir créé ou modifié les fichiers de dictionnaire personnalisés, redémarrez le lanceur de démon de texte intégral SQL à l'aide de la commande suivante :  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  