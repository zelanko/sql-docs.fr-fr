---
title: "Exemple de fichier avec une charge de travail Inline (DTA) d’entrée XML | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: 7c04fe1d-6669-44a1-8b73-36d469e9b002
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: f899682e95e50df8fec87e99507f3bb18308db71
ms.contentlocale: fr-fr
ms.lasthandoff: 10/24/2017

---
# <a name="xml-input-file-sample-with-inline-workload-dta"></a>Exemple de fichier d'entrée XML avec une charge de travail Inline (Assistant Paramétrage de base de données)
  Copiez et collez cet exemple de fichier d'entrée XML qui spécifie une charge de travail avec l'élément **EventString** dans votre éditeur XML ou de texte favori. Vous pouvez utiliser l'élément **EventString** pour spécifier une charge de travail de script [!INCLUDE[tsql](../../includes/tsql-md.md)] dans le fichier d'entrée XML (au lieu d'un fichier de travail distinct). Une fois cet exemple copié dans votre outil d'édition, remplacez les valeurs spécifiées pour les éléments **Server**, **Database**, **Schema**, **Table**, **Workload**, **EventString**et **TuningOptions** par celles dont vous avez besoin pour votre session de paramétrage. Pour plus d’informations sur tous les attributs et éléments enfants que vous pouvez utiliser avec ces éléments, consultez la [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md). L'exemple ci-dessous utilise uniquement un sous-ensemble des options d'attributs et d'éléments enfants disponibles.  
  
## <a name="code"></a>Code  
 [!code-xml[InputFileSamples#InlineWorkloadInputFile](../../tools/dta/codesnippet/xml/xml-input-file-sample-wi_1.xml)]  
  
## <a name="comments"></a>Commentaires  
 `USE database_name` peuvent être spécifiées dans la charge de travail inline contenue dans l'élément **EventString** .  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer et utiliser l'Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)   
 [Afficher et utiliser la sortie de l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)   
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

