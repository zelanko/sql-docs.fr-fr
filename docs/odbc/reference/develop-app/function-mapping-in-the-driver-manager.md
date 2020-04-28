---
title: Mappage de fonction dans le gestionnaire de pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- driver manager [ODBC], function mapping
- functions [ODBC], Unicode functions
ms.assetid: ff093b29-671a-4fc0-86c9-08a311a98e54
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db8e525bb7e8f3e167deb8061a4dd5b75073933c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305580"
---
# <a name="function-mapping-in-the-driver-manager"></a>Mappage des fonctions dans le gestionnaire de pilotes
Le gestionnaire de pilotes prend en charge deux points d’entrée pour les fonctions qui acceptent des arguments de chaîne. La fonction non décorée (**SQLDriverConnect**) est la forme ANSI de la fonction. Le formulaire Unicode est décoré avec un *W* (**SQLDriverConnectW**.)  
  
 Le fichier d’en-tête ODBC prend également en charge les fonctions décorées avec un *A,* (**SQLDriverConnectA**) pour la commodité des applications mixtes ANSI/Unicode. Les appels effectués aux fonctions A sont en fait des appels au point **d'** entrée non décoré (**SQLDriverConnect**.)  
  
 Si l’application est compilée avec le **#define**_UNICODE, le fichier d’en-tête ODBC mappe les appels de fonction non décorés (**SQLDriverConnect**) à la version Unicode (**SQLDriverConnectW**.)  
  
 Le gestionnaire de pilotes reconnaît un pilote comme pilote Unicode si **SQLConnectW** est pris en charge par le pilote.  
  
 Si le pilote est un pilote Unicode, le gestionnaire de pilotes effectue les appels de fonction comme suit :  
  
-   Passe une fonction sans arguments de chaîne ou paramètres directement au pilote.  
  
-   Transmet les fonctions Unicode (avec le suffixe *W* ) directement à l’aide du pilote.  
  
-   Convertit une fonction ANSI (avec le suffixe *a* ) en une fonction Unicode (avec le suffixe *W* ) en convertissant les arguments de chaîne en caractères Unicode et transmet la fonction Unicode au pilote.  
  
 Si le pilote est un pilote ANSI, le gestionnaire de pilotes effectue les appels de fonction comme suit :  
  
-   Transmet des fonctions sans argument de chaîne ou paramètres directement au pilote.  
  
-   Convertit des fonctions Unicode (avec le suffixe *W* ) en un appel de fonction ANSI et les transmet au pilote.  
  
-   Transmet une fonction ANSI directement au pilote.  
  
 Le gestionnaire de pilotes est compatible Unicode en interne. Par conséquent, les performances optimales sont obtenues par une application Unicode utilisant un pilote Unicode, car le gestionnaire de pilotes transmet simplement des fonctions Unicode au pilote. Quand une application ANSI utilise un pilote ANSI, le gestionnaire de pilotes doit convertir les chaînes ANSI en Unicode lors du traitement de certaines fonctions, telles que **SQLDriverConnect**. Après le traitement de la fonction, le gestionnaire de pilotes doit convertir la chaîne Unicode en ANSI avant d’envoyer la fonction au pilote ANSI.  
  
 Une application ne doit pas modifier ou lire ses tampons de paramètres liés lorsque le pilote retourne SQL_STILL_EXECUTING ou SQL_NEED_DATA. Le gestionnaire de pilotes laisse les tampons liés à ANSI jusqu’à ce que le pilote retourne SQL_SUCCESS, SQL_SUCCESS_WITH_INFO ou SQL_ERROR. Une application multithread ne doit pas accéder aux valeurs de paramètre liées sur lesquelles un autre thread exécute une instruction SQL. Le gestionnaire de pilotes convertit les données Unicode en caractères ANSI « sur place », et l’autre thread peut voir les données ANSI dans ces mémoires tampons alors que le pilote continue de traiter l’instruction SQL. Les applications qui lient des données Unicode à un pilote ANSI ne doivent pas lier deux colonnes différentes à la même adresse.
