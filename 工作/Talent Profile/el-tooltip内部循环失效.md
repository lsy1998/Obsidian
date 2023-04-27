在循环外面再加一层
```html
<el-table-column prop="No" label="Score" width="123px">

              <template #default="scope">

                <el-tooltip content="提示信息" placement="top">

                  <div>

                    <svg v-for="item in 5" :key="item" t="1682576702666" class="icon" viewBox="0 0 1024 1024"

                      version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2700" width="20" height="20">

                      <path

                        d="M830.464 63.488q26.624 0 50.176 12.288t41.472 31.232 28.672 43.008 10.752 46.592l0 635.904q0 23.552-11.264 46.592t-30.208 41.472-43.008 30.208-48.64 11.776l-641.024 0q-22.528 0-44.544-10.752t-39.424-28.16-28.16-40.96-10.752-50.176l0-633.856q0-25.6 10.752-50.176t29.696-43.52 43.52-30.208 52.224-11.264l629.76 0z"

                        p-id="2701" :fill="scope.row[1].score >= item ? '#f6ef37' : '#f5f7fa'">

                      </path>

                    </svg>

                  </div>

                </el-tooltip>

              </template>

            </el-table-column>
```
