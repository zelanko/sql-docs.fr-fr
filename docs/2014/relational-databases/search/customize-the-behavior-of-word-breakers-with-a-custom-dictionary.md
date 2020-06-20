---
title: Personnaliser le comportement des analyseurs lexicaux avec un dictionnaire personnalisé | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9fb02a47da20134925d9b2486ea0c08091af4aa6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055506"
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>Personnaliser le comportement des analyseurs lexicaux avec un dictionnaire personnalisé
  Vous pouvez personnaliser le comportement de l'analyseur lexical pour une langue particulière en créant un fichier de dictionnaire personnalisé propre à une langue. Par exemple, vous pouvez empêcher l'analyseur lexical de séparer certains termes ou modèles.  
  
 Pour plus d'informations, consultez l'article SharePoint suivant :  
  
 [Créer un dictionnaire personnalisé (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=215011)  
  
 Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], placez les fichiers de dictionnaire personnalisés dans le dossier suivant :  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 Après avoir créé ou modifié les fichiers de dictionnaire personnalisés, redémarrez le lanceur de démon de texte intégral SQL à l'aide de la commande suivante :  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
