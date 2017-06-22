---
title: "Suppression d’une Extension de traitement de données | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: e59120a2297617d9234dac070cb5c99b4d564d65
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="removing-a-data-processing-extension"></a>Suppression d'une extension pour le traitement des données
  Pour supprimer une extension de traitement de données, supprimez simplement le **Extension** élément pour votre extension de traitement des données à partir du fichier de configuration. Si vous avez entrées pour un serveur de rapports, ainsi que le Concepteur de rapports, supprimez le **Extension** élément à partir de fichiers RSReportServer.config et RSReportDesigner.config. Une fois les informations de configuration supprimées, l'extension pour le traitement des données n'est plus accessible au composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implémentation d’une Extension de traitement des données](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
