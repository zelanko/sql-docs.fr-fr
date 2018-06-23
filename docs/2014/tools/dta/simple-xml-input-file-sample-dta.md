---
title: Exemple de fichier (DTA) d’entrée XML simple | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: 5b00e4eb-1742-43ec-98d8-d84216b6b840
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a95a5c086d5c9c941407e6e3a92e2ea4f8cdcd72
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044390"
---
# <a name="simple-xml-input-file-sample-dta"></a>Exemple de fichier d'entrée XML simple (DTA)
  Copiez et collez cet exemple de fichier d'entrée XML simple à utiliser pour le paramétrage des charges de travail dans votre éditeur XML ou de texte favori. Remplacez ensuite les valeurs spécifiées pour les éléments **Server**, **Database**, **Schema**, **Table**, **Workload**et **TuningOptions** par celles dont vous avez besoin pour votre session de paramétrage. Pour plus d’informations sur les attributs et les éléments enfants que vous pouvez utiliser avec ces éléments, consultez la [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md). L'exemple ci-dessous utilise uniquement un sous-ensemble des options d'attributs et d'éléments enfants disponibles.  
  
## <a name="code"></a>Code  
 [!code-xml[InputFileSamples#SimpleXMLInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#simplexmlinputfile)]  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer et utiliser l'Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)   
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  