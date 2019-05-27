---
title: Se connecter à un fichier Microsoft Excel (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connexcelfile.f1
ms.assetid: 126f7d6b-d270-40e7-b23e-8d114f87065b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e49b37a6f344b7fc6c45c9767a05c7f7d5bfe6e
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66087318"
---
# <a name="connect-to-a-microsoft-excel-file-ssas"></a>Connexion à un fichier Microsoft Excel (SSAS)
  Cette page de l' **Assistant Importation de table** vous permet de vous connecter à un fichier Microsoft Excel stocké sur l'ordinateur local. Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 Pour vous connecter à un fichier Excel, vous devez disposer du fournisseur ACE approprié, installé sur votre ordinateur. Pour plus d’informations, consultez [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](tabular-models/data-sources-supported-ssas-tabular.md).  
  
> [!NOTE]  
>  Les informations d'identification de l'utilisateur actuel sont utilisées lors de la sélection d'un fichier dans cette page. Toutefois, l'importation ne réussira pas si l'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire le fichier sélectionné.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Nom convivial de connexion**  
 Tapez un nom unique pour cette connexion à la source de données. Ce champ est obligatoire.  
  
 **Chemin d’accès du fichier Excel**  
 Spécifiez le chemin d'accès complet du fichier Excel.  
  
 **Parcourir**  
 Accédez à un emplacement dans lequel un fichier Excel est disponible.  
  
 **Avancé**  
 Définissez des propriétés de connexion supplémentaires à partir de la boîte de dialogue **Définir les propriétés avancées** .  
  
 **Utiliser la première ligne comme en-têtes de colonnes**  
 Spécifiez s'il convient d'utiliser la première ligne de données comme en-têtes de colonnes de la table de destination.  
  
 **Tester la connexion**  
 Essayez d'établir une connexion à la source de données à l'aide des paramètres actuels. Un message est affiché pour indiquer si la connexion a abouti.  
  
  
