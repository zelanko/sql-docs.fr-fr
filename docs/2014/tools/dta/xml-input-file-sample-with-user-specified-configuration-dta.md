---
title: Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur (Assistant Paramétrage de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: b29c9716-e5c3-4003-9efb-3ade2197b630
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 166adcb6341ec663816db88169785f71396a7210
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174129"
---
# <a name="xml-input-file-sample-with-user-specified-configuration-dta"></a>Exemple de fichier d'entrée XML avec une configuration spécifiée par l'utilisateur (Assistant Paramétrage de base de données)
  Copiez et collez cet exemple de fichier d’entrée XML qui spécifie une configuration spécifiée par l’utilisateur avec l’élément **Configuration** dans votre éditeur XML ou de texte favori. Vous pouvez ainsi effectuer une évaluation de simulation. Une évaluation de simulation implique l’utilisation de l’élément **Configuration** pour spécifier un ensemble de structures PDS hypothétiques pour la base de données que vous souhaitez paramétrer. Vous pouvez ensuite utiliser l'Assistant Paramétrage du moteur de base de données pour analyser les effets de l'exécution d'une charge de travail dans cette configuration hypothétique en vue de déterminer si elle améliore les performances du traitement des requêtes. Ce type d'analyse offre l'avantage de pouvoir évaluer la nouvelle configuration sans avoir à supporter la charge induite par une mise en œuvre effective. Si votre configuration hypothétique ne permet pas d'améliorer suffisamment les performances, vous pouvez facilement la modifier et l'analyser de nouveau jusqu'à obtention des résultats escomptés.  
  
 Une fois cet exemple copié dans votre outil d'édition, remplacez les valeurs spécifiées pour les éléments **Server**, **Database**, **Schema**, **Table**, **Workload**, **TuningOptions**et **Configuration** par celles dont vous avez besoin pour votre session de paramétrage. Pour plus d’informations sur tous les attributs et éléments enfants que vous pouvez utiliser avec ces éléments, consultez [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md). L'exemple ci-dessous utilise uniquement un sous-ensemble des options d'attributs et d'éléments enfants disponibles.  
  
## <a name="code"></a>Code  
 [!code-xml[InputFileSamples#UserSpecifiedConfigInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#userspecifiedconfiginputfile)]  
  
## <a name="comments"></a>Commentaires  
  
-   La suppression de structures PDS n’est pas prise en charge si vous spécifiez le mode **Absolute** pour l’élément **Configuration** (`Configuration SpecificationMode="Absolute"`).  
  
-   Vous ne pouvez pas créer et supprimer la même structure PDS dans les deux modes (**Relative** ou **Absolute**) de l’élément **Configuration** .  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer et utiliser l'Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)   
 [Afficher et utiliser la sortie de l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)   
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
