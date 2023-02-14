# Execute esses passos para configurar um ambiente:

## Como executar o PubSub emulator:
  obs: Pressupondo que você já tenha instalado: Python. JDK, Google Cloud CLI  
  
  1. `$ gcloud components install pubsub-emulator`
  2. `$ gcloud components update`
  3. `$ gcloud beta emulators pubsub start`

## Como executar o Elasticseach:

  1. `$ docker-compose up`

## O Kibana fica disponível em:
  * Kibana: <http://0.0.0.0:5601/>
  * Sense: <http://localhost:5601/app/sense>
    * Para o Sense connectar com o elasticsearch, utilize no server do sense: `http://es:9200`

## Configurar um index no Elasticseach:

   Esse comando para criar um index "dito-teste" com a mesma config dos indexes de produção:
```
PUT /dito-teste
{
    "settings": {
        "number_of_replicas": 1,
        "number_of_shards": 10
    },
    "mappings": {
        "user": {
            "properties": {
                "reference": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "string",
                    "index": "not_analyzed"
                },
                "api_key": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "name": {
                    "type": "multi_field",
                    "fields": {
                        "name": {
                            "type": "string",
                            "norms": {
                                "enabled": false
                            },
                            "index": "not_analyzed"
                        },
                        "analyzed": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "string"
                        }
                    }
                },
                "email": {
                    "type": "multi_field",
                    "fields": {
                        "email": {
                            "type": "string",
                            "norms": {
                                "enabled": false
                            },
                            "index": "not_analyzed"
                        },
                        "analyzed": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "string"
                        }
                    }
                },
                "id": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "birthday": {
                    "properties": {
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                },
                "phone": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "string",
                    "index": "not_analyzed"
                },
                "gender": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "string",
                    "index": "not_analyzed"
                },
                "first_name": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "string",
                    "index": "not_analyzed"
                },
                "last_name": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "string",
                    "index": "not_analyzed"
                },
                "avatar": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "string",
                    "index": "not_analyzed"
                },
                "description": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "string",
                    "index": "not_analyzed"
                },
                "username": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "string",
                    "index": "not_analyzed"
                },
                "address": {
                    "properties": {
                        "city": {
                            "type": "multi_field",
                            "fields": {
                                "city": {
                                    "type": "string",
                                    "norms": {
                                        "enabled": false
                                    },
                                    "index": "not_analyzed"
                                },
                                "analyzed": {
                                    "norms": {
                                        "enabled": false
                                    },
                                    "type": "string"
                                }
                            }
                        },
                        "country": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "string",
                            "index": "not_analyzed"
                        },
                        "postal_code": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "string",
                            "index": "not_analyzed"
                        },
                        "state": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "string",
                            "index": "not_analyzed"
                        },
                        "street": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "string",
                            "index": "not_analyzed"
                        }
                    }
                },
                "created_at": {
                    "properties": {
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date",
                            "format": "date_optional_time"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                },
                "updated_at": {
                    "properties": {
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date",
                            "format": "date_optional_time"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                },
                "custom_data": {
                    "type": "nested",
                    "properties": {
                        "key": {
                            "type": "string",
                            "norms": {
                                "enabled": false
                            },
                            "index": "not_analyzed"
                        },
                        "string": {
                            "type": "multi_field",
                            "fields": {
                                "string": {
                                    "type": "string",
                                    "norms": {
                                        "enabled": false
                                    },
                                    "index": "not_analyzed"
                                },
                                "analyzed": {
                                    "norms": {
                                        "enabled": false
                                    },
                                    "type": "string"
                                }
                            }
                        },
                        "float": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "float"
                        },
                        "long": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "long"
                        },
                        "boolean": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "boolean"
                        },
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date",
                            "format": "date_optional_time"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                }
            }
        },
        "action": {
            "_parent": {
                "type": "user"
            },
            "properties": {
                "api_key": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "action": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "count": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "long"
                },
                "revenue": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "float"
                },
                "aov": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "float"
                },
                "created_at": {
                    "properties": {
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date",
                            "format": "date_optional_time"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                },
                "updated_at": {
                    "properties": {
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date",
                            "format": "date_optional_time"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                }
            }
        },
        "revenue": {
            "_parent": {
                "type": "user"
            },
            "properties": {
                "api_key": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "count": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "long"
                },
                "revenue": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "float"
                },
                "aov": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "float"
                },
                "created_at": {
                    "properties": {
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date",
                            "format": "date_optional_time"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                },
                "updated_at": {
                    "properties": {
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date",
                            "format": "date_optional_time"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                }
            }
        },
        "network": {
            "_parent": {
                "type": "user"
            },
            "properties": {
                "api_key": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "id": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "type": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                }
            }
        },
        "device": {
            "_parent": {
                "type": "user"
            },
            "properties": {
                "api_key": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "type": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "token": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "created_at": {
                    "properties": {
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date",
                            "format": "date_optional_time"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                },
                "updated_at": {
                    "properties": {
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date",
                            "format": "date_optional_time"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                }
            }
        },
        "event": {
            "_parent": {
                "type": "user"
            },
            "properties": {
                "action": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "string",
                    "index": "not_analyzed"
                },
                "reference": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "api_key": {
                    "type": "string",
                    "index": "not_analyzed",
                    "norms": {
                        "enabled": false
                    }
                },
                "revenue": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "float"
                },
                "currency": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "string",
                    "index": "not_analyzed"
                },
                "value": {
                    "norms": {
                        "enabled": false
                    },
                    "type": "float"
                },
                "created_at": {
                    "properties": {
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date",
                            "format": "date_optional_time"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                },
                "os": {
                    "properties": {
                        "name": {
                            "type": "string",
                            "index": "not_analyzed",
                            "norms": {
                                "enabled": false
                            }
                        },
                        "version": {
                            "type": "string",
                            "index": "not_analyzed",
                            "norms": {
                                "enabled": false
                            }
                        }
                    }
                },
                "browser": {
                    "properties": {
                        "name": {
                            "type": "string",
                            "index": "not_analyzed",
                            "norms": {
                                "enabled": false
                            }
                        },
                        "version": {
                            "type": "string",
                            "index": "not_analyzed",
                            "norms": {
                                "enabled": false
                            }
                        }
                    }
                },
                "platform": {
                    "properties": {
                        "name": {
                            "type": "string",
                            "index": "not_analyzed",
                            "norms": {
                                "enabled": false
                            }
                        },
                        "type": {
                            "type": "string",
                            "index": "not_analyzed",
                            "norms": {
                                "enabled": false
                            }
                        }
                    }
                },
                "utm": {
                    "properties": {
                        "source": {
                            "type": "string",
                            "index": "not_analyzed",
                            "norms": {
                                "enabled": false
                            }
                        },
                        "medium": {
                            "type": "string",
                            "index": "not_analyzed",
                            "norms": {
                                "enabled": false
                            }
                        },
                        "campaign": {
                            "type": "string",
                            "index": "not_analyzed",
                            "norms": {
                                "enabled": false
                            }
                        }
                    }
                },
                "target": {
                    "properties": {
                        "id": {
                            "type": "multi_field",
                            "fields": {
                                "id": {
                                    "type": "string",
                                    "norms": {
                                        "enabled": false
                                    },
                                    "index": "not_analyzed"
                                },
                                "analyzed": {
                                    "norms": {
                                        "enabled": false
                                    },
                                    "type": "string"
                                }
                            }
                        },
                        "title": {
                            "type": "multi_field",
                            "fields": {
                                "title": {
                                    "type": "string",
                                    "norms": {
                                        "enabled": false
                                    },
                                    "index": "not_analyzed"
                                },
                                "analyzed": {
                                    "norms": {
                                        "enabled": false
                                    },
                                    "type": "string"
                                }
                            }
                        },
                        "url": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "string",
                            "index": "not_analyzed"
                        },
                        "type": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "string",
                            "index": "not_analyzed"
                        },
                        "description": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "string",
                            "index": "not_analyzed"
                        },
                        "image": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "string",
                            "index": "not_analyzed"
                        }
                    }
                },
                "custom_data": {
                    "type": "nested",
                    "properties": {
                        "key": {
                            "type": "string",
                            "norms": {
                                "enabled": false
                            },
                            "index": "not_analyzed"
                        },
                        "string": {
                            "type": "multi_field",
                            "fields": {
                                "string": {
                                    "type": "string",
                                    "norms": {
                                        "enabled": false
                                    },
                                    "index": "not_analyzed"
                                },
                                "analyzed": {
                                    "norms": {
                                        "enabled": false
                                    },
                                    "type": "string"
                                }
                            }
                        },
                        "float": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "float"
                        },
                        "long": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "long"
                        },
                        "boolean": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "boolean"
                        },
                        "date": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "date",
                            "format": "date_optional_time"
                        },
                        "day": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "month": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "byte"
                        },
                        "year": {
                            "norms": {
                                "enabled": false
                            },
                            "type": "short"
                        }
                    }
                }
            }
        }
    }
}
```
