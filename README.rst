==============
Pycnpj-crawler
==============

Descrição:
----------

Esse módulo busca nos sites de cada estado os dados de um CNPJ. Veja abaixo o(s) estado(s) suportado(s).

**Somente Python 3!**

.. image:: https://travis-ci.org/matheuscas/pycnpj-crawler.svg?branch=master
    :target: https://travis-ci.org/matheuscas/pycnpj-crawler
.. image:: https://codecov.io/gh/matheuscas/pycnpj-crawler/branch/master/graph/badge.svg
  :target: https://codecov.io/gh/matheuscas/pycnpj-crawler
.. image:: https://badge.fury.io/py/pycnpj-crawler.svg
    :target: https://badge.fury.io/py/pycnpj-crawler
    
Projetos relacionados:
----------------------
- `pycpfcnpj <https://github.com/matheuscas/pycpfcnpj>`_ - Módulo python para validar e gerar números de CPF e CNPJ.


Como instalar:
--------
.. code-block:: shell

   pip install pycnpj-crawler

Como usar:
----------
.. code-block:: python

   from pycnpj_crawler import crawler
   cnpj = "00342735000101"
   estado = "ba"
   resultado = crawler.get_cnpj_data(cnpj, estado)


Exemplo de retorno dos dados de um CNPJ:
--------
.. code-block:: python

    {
        "cnpj":"",
        "inscricao_estadual":"",
        "razao_social":"",
        "nome_fantasia":"",
        "natureza_juridica":"",
        "unidade_de_atendimento":"",
        "unidade_de_fiscalizacao":"",
        "endereco":{
            "numero":"",
            "complemento":"",
            "bairro_distrito":"",
            "cep":"",
            "municipio":"",
            "uf":"",
            "telefone":"",
            "email":"",
            "referencia":"",
            "localizacao":""
    },
        "atividades":{
            "principal":{
                "id":" ",
                "descricao":""
            }
        }
    }

Nem todos os dados podem estar disponíveis, pois depende de cada estado. 

Estados disponíveis:
--------------------
- Bahia (ba) 

Como adicionar um novo estado:
------------------------------

1 - Adicione um modulo do novo estado no pacote `states <https://github.com/matheuscas/pycnpj-crawler/tree/master/pycnpj_crawler/states>`_ nomeando-o com a sigla do estado, por exemplo,
**sp.py** ou **pb.py**.

2 - Adicione a classe do estado no mapeamento em `states.util.py <https://github.com/matheuscas/pycnpj-crawler/blob/master/pycnpj_crawler/states/util.py>`_: 

.. code-block:: python
    BA = "ba"
    PB = "pb" #novo estado

    _states_mapping = {}
    _states_mapping[BA] = "Bahia"
    _states_mapping[PB] = "Paraiba"

O módulo do estado é carregado dinâmicamente usando esse mapeamento. 

3 - A classe do seu estado tem que ter, pelo menos, o seguinte método que recebe o número
do CNPJ. 

.. code-block:: python

   def get_cnpj_data(self, cnpj):
      pass


Esse é um **trabalho em progresso** e toda ajuda é bem vinda. 

==============
Pycnpj-crawler
==============

English version comming soon. 
