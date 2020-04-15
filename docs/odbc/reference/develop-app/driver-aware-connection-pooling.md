---
title: Mise en commun des connexions de conducteur-conscientes (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 53e7e3f7-edab-4d0b-8943-45442ba3ebc9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 70b70c841f37bd69179137c807c0dadcfd932d2b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287599"
---
# <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes
La mise en commun des connexions consciente du conducteur est une nouvelle fonctionnalité du Driver Manager dans Windows 8. La mise en commun des connexions consciente du conducteur permet aux auteurs de pilotes de personnaliser le comportement de mise en commun des connexions dans leur pilote ODBC.  
  
> [!NOTE]  
>  La mise en commun des connexions consciente du conducteur n’est pas prise en charge par la bibliothèque de curseurs. Une application recevra un message d’erreur si elle tente d’activer la bibliothèque de curseurs via SQLSetConnectAttr, lorsque le conducteur sait que la mise en commun des connexions est activée.  
  
 La mise en commun des connexions consciente du conducteur répond aux problèmes suivants liés à la mise en commun des connexions Driver Manager :  
  
 **Fragmentation de la piscine** Le Driver Manager ne retournera une connexion de la piscine que s’il s’agit d’une correspondance exacte avec la chaîne de connexion d’une nouvelle demande de connexion.  L’une des raisons pour lesquelles le gestionnaire de pilote exige une correspondance exacte est que le gestionnaire de pilote ne comprend pas tous les mots clés de chaîne de connexion spécifiques au conducteur et sa valeur.  Toutefois, certaines valeurs de mots clés de chaîne de connexion (comme le nom de la base de données) peuvent ne pas nécessiter une correspondance exacte, puisque le pilote peut modifier la base de données en moins du temps nécessaire pour ouvrir une nouvelle connexion (le décalage horaire exact dépend de la source de données). Et, les différences dans certains attributs de connexion (tels que SQL_ATTR_CURRENT_CATALOG) peuvent prendre plus de temps à changer que les différences dans d’autres attributs (tels que SQL_ATTR_LOGIN_TIMEOUT). Cela peut également empêcher le gestionnaire de conducteur d’utiliser la connexion réutilisable la moins coûteuse de la piscine. Lorsqu’un pilote doit créer de nombreuses nouvelles connexions, les performances d’une application peuvent diminuer et l’évolutivité de la source de données peut diminuer. La fragmentation de la piscine peut être réduite avec la mise en commun des connexions conscientes du conducteur, car un conducteur peut mieux estimer le coût de réutiliser une connexion dans la piscine pour une demande de connexion.  
  
 **Aucune considération de préférence de demande** Certaines sources de données peuvent ouvrir efficacement de nouvelles connexions (par rapport à la réinitialisation de certains attributs), de sorte qu’une application peut préférer ouvrir une nouvelle connexion au lieu d’essayer de réutiliser une connexion légèrement dépareillée de la piscine et de réinitialiser certaines valeurs (bien que cela puisse être plus lent pendant la phrase de initialisation du pool de connexion). Mais certaines applications peuvent garder la charge du serveur plus petit et ouvrir moins de connexions, bien qu’il puisse y avoir un coût plus élevé pour corriger les décalages pour le comportement correct. Sans mise en commun des connexions conscientes du conducteur, vous ne pouvez pas spécifier efficacement ce type de préférence, car le gestionnaire de conducteur ne reconnaît pas tous les attributs de connexion spécifiques au conducteur. La mise en commun des connexions consciente du conducteur permet à un conducteur d’obtenir la préférence de l’utilisateur (avec un attribut spécifique au conducteur de SQLSetConnectAttr) afin qu’il puisse mieux estimer le coût de réutiliser une connexion à partir de la piscine en fonction de la préférence d’un utilisateur.  
  
 Pour plus d’informations sur la mise en commun des connexions conscientes des conducteurs, voir [Developing Connection-Pool Awareness in an ODBC Driver](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
## <a name="determining-driver-support"></a>Détermination du soutien au conducteur  
 La mise en commun des connexions consciente du conducteur est une caractéristique facultative qu’un conducteur ne peut pas prendre en charge. Pour déterminer si un conducteur le prend en charge, utilisez le SQL_DRIVER_AWARE_POOLING_SUPPORTED *InfoType* de [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
## <a name="how-to-enable-driver-aware-connection-pooling"></a>Comment permettre la mise en commun des connexions conscientes des conducteurs  
 Une application peut utiliser la connaissance de la mise en commun des connexions d’un conducteur en fixant l’attribut SQL_ATTR_CONNECTION_POOLING à SQL_CP_DRIVER_AWARE avec [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Si un conducteur ne prend pas en charge la connaissance du pool de connexion, la mise en commun des connexions Driver Manager sera utilisée (comme si SQL_CP_ONE_PER_HENV avait été spécifiée, au lieu de SQL_CP_DRIVER_AWARE). Les applications ODBC 2.x et 3.x peuvent activer cette fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
