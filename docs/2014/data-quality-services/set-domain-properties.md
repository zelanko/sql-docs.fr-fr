---
title: Définir des propriétés de domaine | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.domainproperties.f1
ms.assetid: 8a3c88ca-31d6-4f75-9aca-cf027c6d9845
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5705838a12d5f8f7518cb2726a4151a71c4a067f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226399"
---
# <a name="set-domain-properties"></a>Définir des propriétés de domaine
  Cette rubrique décrit comment définir des propriétés de domaine dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Pour définir les propriétés d'un domaine, vous devez avoir créé une base de connaissances et un domaine.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour définir les propriétés sur un domaine.  
  
##  <a name="Set"></a> Définir des propriétés de domaine  
  
1.  Définir des propriétés sur un domaine existant en ouvrant une base de connaissances dans l’activité de gestion de domaine (consultez [ouvrir une Base de connaissances](../../2014/data-quality-services/open-a-knowledge-base.md)), puis en sélectionnant le domaine approprié dans le **domaine** liste. La page Propriétés du domaine sera affichée par défaut.  
  
2.  Définir des propriétés sur un nouveau domaine après sa création comme décrit dans [créer un domaine](../../2014/data-quality-services/create-a-domain.md).  
  
3.  Cliquez sur **Terminer** pour terminer l’activité de gestion de domaine, comme décrit dans [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir défini les propriétés de domaine  
 Après avoir défini les propriétés de domaine, vous pouvez effectuer d'autres tâches de gestion des domaines sur le domaine, effectuer une découverte des connaissances pour ajouter des connaissances au domaine ou ajouter une stratégie de correspondance au domaine. Pour plus d’informations, consultez [Effectuer une découverte des connaissances](../../2014/data-quality-services/perform-knowledge-discovery.md), [Gestion d’un domaine](../../2014/data-quality-services/managing-a-domain.md) ou [Créer une stratégie de correspondance](../../2014/data-quality-services/create-a-matching-policy.md).  
  
##  <a name="Properties"></a> Propriétés du domaine  
  
###  <a name="Name"></a> Nom et description du domaine  
 Une fois qu'un domaine a été créé, le nom ou la description du domaine peut être modifié. Le nom de domaine doit être unique pour la base de connaissances. La description peut comporter jusqu'à 256 caractères.  
  
###  <a name="Type"></a> Type de données  
 Lorsque vous créez le domaine, sélectionnez l'un des types de données suivants pour les valeurs du domaine : **Chaîne** (valeur par défaut), **Date**, **Entier**, ou **Décimal**. Après avoir créé le domaine, vous pouvez afficher le type de données, mais vous ne pouvez pas le modifier. Le type de données sélectionné pour un domaine définit le type de données source qui peut être mappé au domaine. Pour plus d’informations sur les types de données pris en charge pour chacun des quatre types de données de domaine dans DQS, consultez [Types de données SQL Server et SSIS pris en charge pour les domaines DQS](../../2014/data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md).  
  
###  <a name="Leading"></a> Utiliser des valeurs de début  
 Activez cette case à cocher pour spécifier que la valeur de début dans un groupe de synonymes sera générée au lieu d'une valeur qui en est un synonyme. Désélectionnez **Utiliser des valeurs de début** pour spécifier que chaque valeur de synonyme est générée sous sa forme correcte ou corrigée, et n'est pas remplacée par la valeur de début de son groupe.  
  
###  <a name="Normalize"></a> Normaliser la chaîne  
 Si le type de données est **String**, cliquez pour ignorer les caractères spéciaux dans la source de données pour le traitement de qualité des données par DQS. DQS remplace en interne les caractères spéciaux par une valeur Null ou un espace lorsque les données sont chargées dans le domaine. Un signe deux-points, un trait d'union, un point, un guillemet ou un point-virgule est remplacé par un espace. Un guillemet simple est remplacé par une valeur Null. L'utilisation de la valeur Null réunit les deux parties de la chaîne.  
  
 Le fait d'ignorer les caractères spéciaux dans une valeur de chaîne peut augmenter la précision de la correspondance. Le score de similarité entre deux chaînes peut être augmenté en remplaçant les caractères spéciaux par une valeur Null ou un espace. Les signes de ponctuation ou d'autres symboles peuvent être facilement différents dans différentes chaînes. Le remplacement des caractères spéciaux en interne permet de dépasser le seuil de correspondance minimal du score dans DQS, ainsi, deux chaînes peuvent être considérées comme des correspondances alors qu'elles ne l'auraient pas été sinon. Toutefois, le choix d'ignorer les caractères spéciaux peut dépendre du type des données sur lesquelles vous effectuez la correspondance. Par exemple, lorsque vous utilisez des données dans le système de mesure anglais, le fait d'ignorer les guillemets doubles et les guillemets simples dans les données de produit peut entraîner des faux positifs si un guillemet représente un pouce et qu'un guillemet simple représente un pied.  
  
 La normalisation est effectuée lorsque les données sont chargées et indexées dans les étapes de traitement des données de la découverte, la stratégie de correspondance, le projet de correspondance et les activités de projet de nettoyage. En cas d'activation, la normalisation et la transformation des relations à base de termes sont toutes deux effectuées dans une étape de prétraitement avant analyse. Elles sont exécutées sur chaque domaine avant que des algorithmes qui calculent la similarité entre les chaînes ne soient appliqués. Si une analyse de domaine composite est demandée, elle sera effectuée avant la normalisation et la transformation des relations à base de termes, car l'analyse de délimiteur requiert des symboles. D'autres opérations, telles que les règles de domaine et les modifications de valeurs de domaine, sont exécutées après les transformations. Les données résultantes ne sont pas modifiées par le remplacement en interne des caractères spéciaux dans DQS.  
  
###  <a name="Format"></a> Mettre en forme la sortie vers  
 Sélectionnez la mise en forme qui est appliquée lorsque les valeurs de données dans le domaine sont générées. La mise en forme est spécifique au type de données sélectionné, comme indiqué dans la liste suivante. La sélection de l'option **Aucun** signifie qu'aucun des formats de la liste ne sera appliqué.  
  
-   Pour une valeur de chaîne, vous pouvez spécifier que la chaîne soit générée en majuscules, en minuscules, ou avec la première lettre en majuscule.  
  
-   Pour une valeur de date, vous pouvez spécifier le format du jour, du mois et de l'année.  
  
-   Pour une valeur entière, vous pouvez spécifier le type de masque de format à appliquer.  
  
-   Pour une valeur décimale, vous pouvez spécifier la précision et le type de masque de format à appliquer.  
  
###  <a name="Language"></a> Langage  
 Si le type de données est **Chaîne**, sélectionnez la langue que vous souhaitez associer au domaine pour passer le vérificateur d'orthographe. Cette sélection s'applique uniquement au vérificateur d'orthographe, car les résultats de ce vérificateur d'orthographe dépendent de la langue utilisée. La sélection s'applique uniquement à un seul domaine dont le type de données est chaîne. La propriété de langue n'est pas pertinente pour les domaines composites. La langue pour chaque partie d'un domaine composite est déterminée par le domaine unique approprié.  
  
 La langue par défaut est l'anglais. Si vous affectez à la propriété **Langue** la valeur **Autre** , le vérificateur d'orthographe est désactivé pour le domaine.  
  
> [!TIP]  
>  Si la langue n'est pas répertoriée dans la liste déroulante **Langue** , vous devez sélectionner **Autre**. Cela garantit que DQS nettoie et élimine les doublons des données de langue non répertoriées selon les informations dont il dispose (règles de domaine, valeurs de domaine, TBR, règle de correspondance) dans le domaine.  
  
###  <a name="Speller"></a> Activer le vérificateur d'orthographe  
 Si le type de données est **Chaîne**, cliquez pour activer le vérificateur d'orthographe DQS pour le domaine. Le vérificateur d'orthographe fonctionne uniquement sur les domaines dont le type de données est chaîne. La case à cocher **Activer le vérificateur d'orthographe** active le vérificateur d'orthographe uniquement pour le seul domaine associé à la case à cocher. La case à cocher ne s'applique pas à un domaine composite.  
  
 Le vérificateur d'orthographe propose des corrections de syntaxe et de validation pour les valeurs du domaine. Pour plus d’informations, consultez [utiliser le vérificateur d’orthographe DQS](../../2014/data-quality-services/use-the-dqs-speller.md).  
  
###  <a name="Syntax"></a> Désactiver les algorithmes d'erreur de syntaxe  
 Si le type de données est **Chaîne**, activez cette case à cocher pour spécifier que les erreurs de syntaxe ne sont pas identifiées par DQS dans le domaine lors du nettoyage. Activez cette case à cocher lorsque l'identification des erreurs de syntaxe pour ce domaine n'est pas nécessaire. Par exemple, l'identification des erreurs de syntaxe peut ne pas être importante pour un numéro de série. Ce contrôle est uniquement disponible pour le type de données chaîne. DQS ne recherche pas les erreurs de syntaxe dans les types de données autres que chaîne.  
  
  
