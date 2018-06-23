---
title: Se connecter à une Source de données (SSAS) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.conndatasource.f1
ms.assetid: 1e2b17e9-092b-4af1-8a58-c52b8fe10ff1
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f33af08d91f2c8e739c9295daed0ae47563ede51
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044862"
---
# <a name="connect-to-a-data-source-ssas"></a>Connexion à une source de données (SSAS)
  Cette page de l' **Assistant Importation de table** vous permet de créer une connexion à diverses sources de données, telles que des bases de données relationnelles, des flux de données et des fichiers. Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 Pour vous connecter à une source de données, vous devez disposer du fournisseur approprié, installé sur votre machine. Le fournisseur approprié doit également être installé sur le serveur de base de données d'espace de travail. Pour les serveurs 32 bits (x86), les fournisseurs 32 bits doivent être installés. Pour les serveurs 64 bits (x64), les fournisseurs 64 bits doivent être installés.  
  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] s’exécute toujours dans un processus 32 bits, indépendamment de l’architecture. Lorsque vous exécutez [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] sur un ordinateur 64 bits, vous devez veiller aux points suivants lors de l'installation des fournisseurs de données :  
  
-   Pour les fournisseurs qui prennent en charge l'installation côte à côte des fournisseurs 32 bits et 64 bits, vous devez installer les deux fournisseurs.  
  
-   Pour le fournisseur ACE, vous devez installer la version 64 bits du fournisseur. Étant donné qu'Office installe automatiquement le fournisseur ACE, vous ne devez pas exécuter la version 32 bits de Microsoft Office sur un ordinateur 64 bits qui héberge le serveur de base de données d'espace de travail.  
  
     Le fournisseur ACE est utilisé pour importer à partir de fichiers texte, Excel et Access. Si la prise en charge de ces sources de données n'est pas nécessaire, vous pouvez exécuter une version 32 bits de Microsoft Office sur un ordinateur qui exécute un serveur de base de données d'espace de travail 64 bits.  
  
-   Pour les autres fournisseurs qui ne prennent pas en charge l'installation côte à côte des fournisseurs 32 bits et 64 bits, vous devez installer le fournisseur 32 bits. Si seuls les ordinateurs 64 bits sont disponibles, vous devez utiliser un ordinateur distant avec un fournisseur 64 bits installé comme serveur de base de données d'espace de travail.  
  
  