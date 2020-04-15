---
title: Utilisation d’applications 16-Bit et 32-Bit avec des pilotes 32-Bit Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307610"
---
# <a name="using-16-bit-and-32-bit-applications-with-32-bit-drivers"></a>Utilisation d’applications 16 bits et 32 bits avec des pilotes 32 bits
> [!IMPORTANT]  
>  Le support d’application 16 bits sera supprimé dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Développez plutôt des applications 32 ou 64 bits.  
  
 Avec le composant d’accès aux données ODBC, vous pouvez utiliser des applications 16 bits et 32 bits avec des pilotes 32 bits. Les systèmes d® Microsoft ® Windows® 95/98 et Microsoft Windows NT®/Windows 2000 prennent en charge les combinaisons suivantes d’applications et de pilotes :  
  
-   Applications 16 bits avec pilotes 32 bits  
  
-   Applications 32 bits avec pilotes 32 bits  
  
 L’utilisation d’une application 32 bits avec un pilote 16 bits n’est pas prise en charge.  
  
> [!NOTE]  
>  Commençant par la sortie de la version 3.0 d’ODBC, Windows NT 4.0 a été pris en charge.  
  
 ODBC inclut les composants ODBC nécessaires pour prendre en charge les configurations ci-dessus en « hunking » bibliothèques à liaison dynamique (DLL) pour convertir les adresses 16 bits en adresses 32 bits et vice versa. Le programme De configuration détermine le système d’exploitation que vous utilisez et installe les composants ODBC requis par ce système. Vous pouvez également choisir d’installer les composants ODBC utilisés par tous les systèmes.  
  
 Dans la plupart des cas, le portage d’une application ou d’un conducteur de 16 bits à 32 bits implique cinq types de changements :  
  
-   Modifications apportées au code de traitement des messages  
  
-   Changements parce que les intégreurs et les poignées sont 32 bits  
  
-   Modifications des appels vers les interfaces de programmation d’applications Windows (API)  
  
-   Modifications pour rendre le conducteur en sécurité  
  
-   Modifications apportées aux composants ODBC  
  
 Du point de vue de l’application ou de la programmation du conducteur, la principale différence entre les composants ODBC 16 bits et 32 bits est qu’ils ont des noms de fichiers différents. Du point de vue du système, l’architecture de chaque application ou connexion du conducteur est différente et les outils utilisés pour gérer les sources de données sont différents.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Utilisation d’applications 16 bits avec des pilotes 32 bits](../../odbc/microsoft/using-16-bit-applications-with-32-bit-drivers.md)  
  
-   [Utilisation d’applications 32 bits avec des pilotes 32 bits](../../odbc/microsoft/using-32-bit-applications-with-32-bit-drivers.md)
