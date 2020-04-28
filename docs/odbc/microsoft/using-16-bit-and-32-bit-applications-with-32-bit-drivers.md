---
title: Utilisation d’applications 16 bits et 32 bits avec des pilotes 32 bits | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 16-bit applications
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
- 16-bit applications with 32-bit drivers [ODBC]
ms.assetid: fc65c988-b31f-4cc9-851f-30d2119604fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7ce996a7c4816d4d14491e226f891904b6cf8c02
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307610"
---
# <a name="using-16-bit-and-32-bit-applications-with-32-bit-drivers"></a>Utilisation d’applications 16 bits et 32 bits avec des pilotes 32 bits
> [!IMPORTANT]  
>  la prise en charge des applications 16 bits sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Développez des applications 32 bits ou 64 bits à la place.  
  
 Le composant d’accès aux données ODBC vous permet d’utiliser des applications 16 bits et 32 bits avec des pilotes 32 bits. Les systèmes d’exploitation Microsoft® Windows® 95/98 et Microsoft Windows NT®/Windows 2000 prennent en charge les combinaisons d’applications et de pilotes suivantes :  
  
-   applications 16 bits avec pilotes 32 bits  
  
-   applications 32 bits avec pilotes 32 bits  
  
 L’utilisation d’une application 32 bits avec un pilote 16 bits n’est pas prise en charge.  
  
> [!NOTE]  
>  Depuis la publication de la version ODBC 3,0, Windows NT 4,0 est pris en charge.  
  
 ODBC comprend les composants ODBC nécessaires à la prise en charge des configurations ci-dessus par « thunking » des bibliothèques de liens dynamiques (dll) pour convertir des adresses 16 bits en adresses 32 bits et vice versa. Le programme d’installation détermine le système d’exploitation que vous utilisez et installe les composants ODBC requis par ce système. Vous pouvez également choisir d’installer les composants ODBC utilisés par tous les systèmes.  
  
 Dans la plupart des cas, le portage d’une application ou d’un pilote de 16 bits à 32 bits implique cinq types de modifications :  
  
-   Modifications apportées au code de gestion des messages  
  
-   Modifications, car les entiers et les handles sont 32 bits  
  
-   Modifications des appels aux interfaces de programmation d’applications (API) Windows  
  
-   Modifications pour rendre le pilote thread-safe  
  
-   Modifications apportées aux composants ODBC  
  
 Du point de vue de la programmation des applications ou des pilotes, la principale différence entre les composants ODBC 16 bits et 32 bits est qu’ils ont des noms de fichiers différents. Du point de vue du système, l’architecture de chaque connexion d’application ou de pilote est différente et les outils utilisés pour gérer les sources de données sont différents.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Utilisation d’applications 16 bits avec des pilotes 32 bits](../../odbc/microsoft/using-16-bit-applications-with-32-bit-drivers.md)  
  
-   [Utilisation d’applications 32 bits avec des pilotes 32 bits](../../odbc/microsoft/using-32-bit-applications-with-32-bit-drivers.md)
