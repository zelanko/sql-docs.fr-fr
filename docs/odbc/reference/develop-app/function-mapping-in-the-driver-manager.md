---
title: Cartographie de fonction dans le gestionnaire de conducteur (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305580"
---
# <a name="function-mapping-in-the-driver-manager"></a>Mappage des fonctions dans le gestionnaire de pilotes
Le gestionnaire de pilote prend en charge deux points d’entrée pour les fonctions qui prennent des arguments de chaîne. La fonction non décodée (**SQLDriverConnect**) est la forme ANSI de la fonction. Le formulaire Unicode est orné d’un *W* (**SQLDriverConnectW**.)  
  
 Le fichier d’en-tête ODBC prend également en charge les fonctions décorées d’un *A,* (**SQLDriverConnectA**) pour la commodité des applications mixtes ANSI/Unicode. Les appels effectués aux fonctions **A** sont en fait des appels dans le point d’entrée non décoré (**SQLDriverConnect**.)  
  
 Si l’application est compilée avec le _UNICODE **#define**, le fichier d’en-tête ODBC cartographiera les appels de fonction non décorés (**SQLDriverConnect**) à la version Unicode (**SQLDriverConnectW**.)  
  
 Le gestionnaire de conducteur reconnaît un conducteur comme un conducteur Unicode si **SQLConnectW** est pris en charge par le conducteur.  
  
 Si le conducteur est un pilote Unicode, le Gestionnaire de conducteur fait des appels de fonction comme suit :  
  
-   Passe une fonction sans arguments de chaîne ou paramètres directement à travers le conducteur.  
  
-   Passe les fonctions Unicode (avec le suffixe *W)* directement à travers le conducteur.  
  
-   Convertit une fonction ANSI (avec le suffixe *A)* en fonction Unicode (avec le suffixe *W)* en convertissant les arguments de chaîne en caractères Unicode et passe la fonction Unicode au pilote.  
  
 Si le conducteur est un pilote ANSI, le Driver Manager fait des appels de fonction comme suit :  
  
-   Passe les fonctions sans arguments de chaîne ou paramètres directement à travers le conducteur.  
  
-   Convertit les fonctions Unicode (avec le suffixe *W)* en un appel de fonction ANSI et le transmet au conducteur.  
  
-   Passe une fonction ANSI directement au conducteur.  
  
 Le Driver Manager est activé en interne par Unicode. Par conséquent, les performances optimales sont obtenues par une application Unicode travaillant avec un pilote Unicode, car le Driver Manager transmet simplement les fonctions Unicode au conducteur. Lorsqu’une application ANSI travaille avec un pilote ANSI, le Driver Manager doit convertir les chaînes de l’ANSI à Unicode lors du traitement de certaines fonctions, telles que **SQLDriverConnect**. Après le traitement de la fonction, le Driver Manager doit ensuite convertir la chaîne Unicode à ANSI avant d’envoyer la fonction au pilote ANSI.  
  
 Une application ne doit pas modifier ou lire ses paramètres de limite lorsque le conducteur retourne SQL_STILL_EXECUTING ou SQL_NEED_DATA. Le Driver Manager laisse les tampons liés à l’ANSI jusqu’à ce que le conducteur revienne SQL_SUCCESS, SQL_SUCCESS_WITH_INFO ou SQL_ERROR. Une application multithreaded ne devrait pas accéder à des valeurs de paramètres consolidées qu’un autre thread exécute une déclaration SQL sur. Le Driver Manager convertit les données d’Unicode à ANSI " en place ", et l’autre thread peut voir les données DE l’ANSI dans ces tampons pendant que le conducteur est toujours en traitement de la déclaration SQL. Les applications qui lient les données Unicode à un pilote ANSI ne doivent pas lier deux colonnes différentes à la même adresse.
