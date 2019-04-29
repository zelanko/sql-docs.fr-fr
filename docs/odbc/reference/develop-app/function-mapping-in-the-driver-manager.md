---
title: Fonction de mappage dans le Gestionnaire de pilotes | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 40dc214fa7f77dfb81c941095ecd71d3d4bf5a36
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63061557"
---
# <a name="function-mapping-in-the-driver-manager"></a>Mappage des fonctions dans le gestionnaire de pilotes
Le Gestionnaire de pilotes prend en charge les deux points d’entrée pour les fonctions qui acceptent des arguments de chaîne. La fonction non décorée (**SQLDriverConnect**) est au format ANSI de la fonction. Le format Unicode est décorée avec un *W* (**SQLDriverConnectW**.)  
  
 Le fichier d’en-tête ODBC prend également en charge les fonctions décorées avec un *A,* (**SQLDriverConnectA**) pour la commodité des applications de ANSI/Unicode mixtes. Les appels effectués à la **A** fonctions sont en fait des appels dans le point d’entrée non décoré (**SQLDriverConnect**.)  
  
 Si l’application est compilée avec le _UNICODE **#define**, le fichier d’en-tête ODBC mappera les appels de fonction non décorée (**SQLDriverConnect**) vers la version Unicode (**SQLDriverConnectW** .)  
  
 Le Gestionnaire de pilotes reconnaît un pilote en tant que Unicode pilote si **SQLConnectW** est pris en charge par le pilote.  
  
 Si le pilote est Unicode, le Gestionnaire de pilotes effectue des appels de fonction comme suit :  
  
-   Passe une fonction sans arguments de chaîne ou des paramètres directement par le biais du pilote.  
  
-   Passe des fonctions Unicode (avec le *W* suffixe) directement via le pilote.  
  
-   Convertit une fonction ANSI (avec le *A* suffixe) à une fonction Unicode (avec le *W* suffixe) en convertissant les arguments de chaîne Unicode caractères et passe la fonction Unicode au pilote.  
  
 Si le pilote est un pilote ANSI, le Gestionnaire de pilotes effectue des appels de fonction comme suit :  
  
-   Transmet les fonctions sans arguments de chaîne ou les paramètres directement par le biais du pilote.  
  
-   Convertit des fonctions Unicode (avec le *W* suffixe) ANSI appel de fonction et le transmet au pilote.  
  
-   Passe une fonction ANSI directement au pilote.  
  
 Le Gestionnaire de pilotes prend en charge Unicode en interne. Par conséquent, les performances optimales sont obtenu par une application Unicode fonctionne avec un pilote Unicode, car le Gestionnaire de pilotes transmet simplement des fonctions Unicode par le biais du pilote. Lorsqu’une application ANSI fonctionne avec un pilote ANSI, le Gestionnaire de pilotes doit convertir des chaînes d’ANSI en Unicode lors du traitement de certaines fonctions, telles que **SQLDriverConnect**. Après le traitement de la fonction, le Gestionnaire de pilotes doit ensuite convertir la chaîne Unicode en ANSI avant l’envoi de la fonction au pilote ANSI.  
  
 Une application ne doit pas modifier ou lire ses tampons de paramètres liés lorsque le pilote retourne SQL_NEED_DATA ou SQL_STILL_EXECUTING. Le Gestionnaire de pilotes laisse les mémoires tampon liées à la norme ANSI jusqu'à ce que le pilote retourne SQL_SUCCESS, SQL_SUCCESS_WITH_INFO ou SQL_ERROR. Une application multithread ne doit pas accéder à toutes les valeurs de paramètre lié un autre thread s’exécute une instruction SQL. Le Gestionnaire de pilotes convertit les données Unicode en ANSI « sur place », et l’autre thread peut s’afficher des données ANSI dans ces mémoires tampons pendant que le pilote traite toujours l’instruction SQL. Applications qui lient des données Unicode à un pilote ANSI ne doivent pas lier deux colonnes différentes à la même adresse.
