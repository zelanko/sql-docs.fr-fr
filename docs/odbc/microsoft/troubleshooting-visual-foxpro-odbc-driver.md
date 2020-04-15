---
title: Dépannage (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set ANSI [ODBC]
- troubleshooting Visual FoxPro ODBC driver [ODBC]
- remote views [ODBC]
- multitiered views [ODBC]
- parameterized views [ODBC], Visual FoxPro ODBC driver
- fetches [ODBC], Visual FoxPro ODBC driver
- positioned updates [ODBC]
- background fetching [ODBC]
ms.assetid: fd478dd8-666a-4f0a-a2d6-b94e81cbbe4b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 70b035069c0be88d05a3aa5e17b96af991c27405
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303030"
---
# <a name="troubleshooting-visual-foxpro-odbc-driver"></a>Résolution des problèmes (pilote ODBC Visual FoxPro)
Les sections suivantes discutent de la façon d’améliorer les performances et de résoudre les problèmes que vous pourriez rencontrer lors de l’utilisation du pilote Visual FoxPro ODBC.  
  
## <a name="accessing-parameterized-views"></a>Accès aux vues paramétrisées  
 Vous ne pouvez pas accéder aux vues paramétrisées dans une base de données Visual FoxPro à l’aide du pilote. Une vue paramétrée crée une clause WHERE dans l’énoncé SQL **SELECT** de la vue qui limite les enregistrements téléchargés aux enregistrements qui répondent aux conditions de la clause WHERE construite en utilisant la valeur fournie pour le paramètre. Étant donné que le conducteur ne prend pas en charge le passage des paramètres de la vue, les tentatives d’accès à une vue paramétrée en utilisant le conducteur échoueront.  
  
 La valeur du paramètre peut être fournie au moment de l’exécution ou transmise de façon programmatique à la vue.  
  
## <a name="accessing-remote-views"></a>Accès aux vues à distance  
 Vous ne pouvez pas accéder à des vues distantes dans une base de données Visual FoxPro à l’aide du pilote. Les vues à distance sont des vues qui accèdent soit aux données non FoxPro, soit à une combinaison de données FoxPro et non FoxPro. Pour accéder à des vues à distance, utilisez Visual FoxPro.  
  
## <a name="deleting-records"></a>Suppression des dossiers  
 Vous pouvez marquer les enregistrements de suppression à l’aide du pilote, mais vous ne pouvez pas supprimer définitivement les enregistrements de la base de données. Pour supprimer définitivement les enregistrements d’une table, utilisez Visual FoxPro.  
  
## <a name="increasing-performance-using-background-fetching"></a>Accroître les performances en utilisant l’utilisation de l’arrière-plan  
 Vous pouvez améliorer les performances sur les gros lots en utilisant la fonction d’aller chercher de fond du conducteur. L’aller chercher de fond utilise un thread séparé pour récupérer les données demandées auprès d’une source de données spécifique.  
  
 Vous pouvez utiliser l’utilisation d’un bagage d’arrière-plan pour une source de données de l’une des façons suivantes :  
  
-   Vérifiez les données Fetch dans la case à cocher **d’arrière-plan** sur la [boîte de dialogue ODBC Visual FoxPro Setup](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md).  
  
-   Utilisez le mot clé d’attribut BackgroundFetch dans votre chaîne de connexion.  
  
 Pour plus d’informations sur les mots clés d’attribut de chaîne de connexion, voir [Using Connection Strings](../../odbc/microsoft/using-connection-strings.md).  
  
## <a name="updating-multitiered-views"></a>Mise à jour des vues multitiers  
 Une vue à plusieurs étages est une vue basée sur une ou plusieurs vues plutôt que sur une table de base. Lorsque vous mettez à jour les données dans une vue multitier, les mises à jour ne diminuent qu’à un niveau, à la vue sur laquelle la vue de haut niveau est basée ; les tables de base ne sont pas mises à jour.  
  
## <a name="using-data-definition-language-ddl-in-stored-procedures"></a>Utilisation du langage de définition des données (DDL) dans les procédures stockées  
 Vous ne pouvez pas utiliser DDL, comme CREATE TABLE ou ALTER TABLE, dans visual FoxPro procédures stockées.  
  
 Pour plus d’informations sur la langue que vous pouvez utiliser dans les procédures stockées, consultez [Support for Rules, Triggers, Default Values, and Stored Procedures](../../odbc/microsoft/support-rules-triggers-defaults-stored-procedures-visual-foxpro-odbc-driver.md).  
  
## <a name="using-positioned-updates"></a>Utilisation des mises à jour positionnées  
 Le conducteur ne prend pas en charge les mises à jour positionnées. Utilisez la clause SQL WHERE pour identifier les lignes que vous souhaitez mettre à jour.  
  
## <a name="using-the-set-ansi-command"></a>Utilisation du commandement SET ANSI  
 Si vous êtes un développeur Visual FoxPro, vous devez être conscient que le paramètre par défaut pour SET ANSI est ON pour le pilote, contrairement à un paramètre par défaut de OFF pour Visual FoxPro. Le paramètre PAR défaut ON pour SET ANSI permet aux sources de données Visual FoxPro de se comporter de manière cohérente avec d’autres sources de données ODBC qui effectuent généralement des comparaisons exactes. Vous pouvez modifier le paramètre par défaut. Pour plus d’informations, voir [SET ANSI](../../odbc/microsoft/set-ansi-command.md).
