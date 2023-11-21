<template>
  <div class="about">
    <h1>This is an Post Number page</h1>
    <!--郵遞區號-->
    <template v-if="disSelect !== null">
      {{ districts[disSelect].zip }}
    </template>
    <!--縣市選擇-->
    <select v-model="citySelect">
      <option :value="null">請選擇</option>
      <option v-for="(city, index) of cities" :value="index" :key="city">{{ city }}</option>
    </select>
    <!--行政區選擇-->
    <select v-model="disSelect">
      <option :value="null">請選擇</option>
      <!-- <option v-for="dis of districts" :value="dis.zip" :key="dis.name">{{ dis.name }}</option> -->
      <option v-for="(dis, index) of districts" :value="index" :key="dis.name">{{ dis.name }}</option>
    </select>
  </div>
</template>

<script>
const postDataCH = require('@/assets/post.json')
const postDataEN = require('@/assets/postEN.json')
export default {
  data () {
    return {
      lang: 0, // 0=> 中文,1=>英文
      citySelect: null,
      disSelect: null,
      allTagsData: {
        價值分群: {
          type: 'multiple',
          data: {
            新客客群: {
              type: 'end',
              data: {},
              moreOption: {
                unit: '',
                type: []
              }
            },
            高價值客群: {
              type: 'end',
              data: {},
              moreOption: {
                unit: '',
                type: []
              }
            },
            忠誠客群: {
              type: 'end',
              data: {},
              moreOption: {
                unit: '',
                type: []
              }
            },
            沉睡客群: {
              type: 'end',
              data: {},
              moreOption: {
                unit: '',
                type: []
              }
            },
            流失客群: {
              type: 'end',
              data: {},
              moreOption: {
                unit: '',
                type: []
              }
            }
          },
          moreOption: {
            unit: '',
            type: []
          }
        },
        基本屬性: {
          type: 'single',
          data: {
            性別: {
              type: 'multiple',
              data: {
                男性: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: []
                  }
                },
                女性: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: []
                  }
                }
              },
              moreOption: {
                unit: '',
                type: []
              }
            },
            年齡級距: {
              type: 'range_歲',
              data: {},
              moreOption: {
                unit: '',
                type: []
              }
            },
            生日: {
              type: 'multiple',
              data: {
                一月: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: []
                  }
                },
                二月: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: []
                  }
                },
                三月: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: []
                  }
                }
              },
              moreOption: {
                unit: '',
                type: []
              }
            },
            城市: {
              type: 'api',
              data: {},
              moreOption: {
                unit: '',
                type: []
              }
            },
            線下門市名稱: {
              type: 'api',
              data: {},
              moreOption: {
                unit: '',
                type: []
              }
            },
            會員等級: {
              type: 'multiple',
              data: {
                A: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: []
                  }
                },
                B: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: []
                  }
                },
                C: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: []
                  }
                }
              },
              moreOption: {
                unit: '',
                type: []
              }
            },
            註冊管道: {
              type: 'api',
              data: {},
              moreOption: {
                unit: '',
                type: []
              }
            },
            註冊日期: {
              type: 'dateRange',
              data: {},
              moreOption: {
                unit: '',
                type: []
              }
            },
            會員品牌歸屬: {
              type: 'api',
              data: {},
              moreOption: {
                unit: '',
                type: []
              }
            }
          },
          moreOption: {
            unit: '',
            type: []
          }
        },
        渠道再行銷: {
          type: 'single',
          data: {
            Email: {
              type: 'single',
              data: {
                互動評級: {
                  type: 'multiple',
                  data: {
                    高: {
                      type: 'end',
                      data: {},
                      moreOption: {
                        unit: '',
                        type: []
                      }
                    },
                    中: {
                      type: 'end',
                      data: {},
                      moreOption: {
                        unit: '',
                        type: []
                      }
                    },
                    低: {
                      type: 'end',
                      data: {},
                      moreOption: {
                        unit: '',
                        type: []
                      }
                    }
                  },
                  moreOption: {
                    unit: '',
                    type: []
                  }
                },
                可寄送名單: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: []
                  }
                },
                有寄出過: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['event']
                  }
                }
              },
              moreOption: {
                unit: '',
                type: []
              }
            },
            SMS: {
              type: 'single',
              data: {
                互動評級: {
                  type: 'multiple',
                  data: {
                    高: {
                      type: 'end',
                      data: {},
                      moreOption: {
                        unit: '',
                        type: []
                      }
                    },
                    中: {
                      type: 'end',
                      data: {},
                      moreOption: {
                        unit: '',
                        type: []
                      }
                    },
                    低: {
                      type: 'end',
                      data: {},
                      moreOption: {
                        unit: '',
                        type: []
                      }
                    }
                  },
                  moreOption: {
                    unit: '',
                    type: []
                  }
                },
                可寄送名單: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: []
                  }
                },
                有寄出過: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['event']
                  }
                }
              },
              moreOption: {
                unit: '',
                type: []
              }
            }
          },
          moreOption: {
            unit: '',
            type: []
          }
        },
        網站行為: {
          type: 'single',
          data: {
            網站1: {
              type: 'single',
              data: {
                造訪商品名稱: {
                  type: 'api',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time', 'count']
                  }
                },
                造訪商品類別: {
                  type: 'api',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time', 'count']
                  }
                },
                造訪品牌名稱: {
                  type: 'api',
                  data: {},
                  moreOption: {
                    unit: '造訪',
                    type: ['time', 'count']
                  }
                },
                造訪頁面類別: {
                  type: 'api',
                  data: {},
                  moreOption: {
                    unit: '點擊',
                    type: ['time', 'count']
                  }
                },
                有造訪過網站: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '造訪',
                    type: ['time', 'count']
                  }
                },
                有購買的人: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time', 'count', 'cost']
                  }
                },
                有登入過: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '登入',
                    type: ['time', 'count']
                  }
                },
                有加入購物車但未結: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time']
                  }
                },
                平均瀏覽時長: {
                  type: 'range_分',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time']
                  }
                },
                utm_campaign_source: {
                  type: 'api',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time']
                  }
                }
              },
              moreOption: {
                unit: '',
                type: []
              }
            },
            網站2: {
              type: 'single',
              data: {
                造訪商品名稱: {
                  type: 'api',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time', 'count']
                  }
                },
                造訪商品類別: {
                  type: 'api',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time', 'count']
                  }
                },
                造訪品牌名稱: {
                  type: 'api',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time', 'count']
                  }
                },
                造訪頁面類別: {
                  type: 'api',
                  data: {},
                  moreOption: {
                    unit: '點擊',
                    type: ['time', 'count']
                  }
                },
                有造訪過網站: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '造訪',
                    type: ['time', 'count']
                  }
                },
                有購買的人: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time', 'count', 'cost']
                  }
                },
                有登入過: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time', 'count']
                  }
                },
                有加入購物車但未結: {
                  type: 'end',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time']
                  }
                },
                平均瀏覽時長: {
                  type: 'range_分',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time']
                  }
                },
                utm_campaign_source: {
                  type: 'api',
                  data: {},
                  moreOption: {
                    unit: '',
                    type: ['time']
                  }
                }
              },
              moreOption: {
                unit: '',
                type: []
              }
            }
          },
          moreOption: {
            unit: '',
            type: []
          }
        }
      }
    }
  },
  computed: {
    postData () {
      return this.lang === 0 ? postDataCH : postDataEN
    },
    // cityComputed: {
    //   get () {
    //     return this.citySelect
    //   },
    //   set (val) {
    //     this.citySelect = val
    //     // this.disSelect = null
    //     if (this.disSelect >= postData[val].districts.length) this.disSelect = 0
    //   }
    // },
    cities () {
      return this.postData.map((item) => {
        return item.name
      })
    },
    districts () {
      let districts = []
      if (this.citySelect !== null) {
        districts = this.postData[this.citySelect].districts
      }
      return districts
    }
  },
  watch: {
    citySelect (nVal, oVal) {
      // this.disSelect = null
      if (this.disSelect >= this.postData[this.citySelect].districts.length) this.disSelect = 0
    }
  }
}
</script>
