<template>
  <div class="bg-white rounded" style="width: 100%; height: 845px">
    <!-- Head Priorities List -->
    <div class="bg-white rounded px-5 py-3">
      <h1>Priorities List</h1>
    </div>

    <!-- body Priorities List -->
    <div class="py-5 px-5">
      <CButton class="px-5" variant="ghost">User</CButton>
      <CButton class="px-5" variant="ghost">Priority</CButton>

      <!-- Search bar -->
      <div class="container pt-5">
        <div class="row justify-content-center">
          <div class="col-md-6">
            <form class="form-inline">
              <div class="input-group">
                <input
                  type="text"
                  class="form-control rounded-start-pill"
                  placeholder="Search"
                />
                <div class="input-group-append">
                  <button
                    class="btn btn-primary rounded-start-0 rounded-end-circle"
                    type="submit"
                  >
                    <CIcon :icon="icon.cilMagnifyingGlass" size="xl" />
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <!-- End Search bar -->

      <!-- Smart Table -->
                  <CSmartTable
                    :active-page="3"
                    cleaner
                    column-filter
                    column-sorter
                    :columns="columns"
                    clickable-rows
                    footer
                    header
                    :items-per-page="5"
                    items-per-page-select
                    :items="items"
                    pagination
                    table-filter
                    :table-props="{
                      striped: true,
                      hover: true,
                    }"
                  >
                    <template #status="{ item }">
                      <td>
                        <CBadge :color="getBadge(item.status)">{{
                          item.status
                        }}</CBadge>
                      </td>
                    </template>
                    <template #show_details="{ item, index }">
                      <td class="py-2">
                        <CButton
                          color="primary"
                          variant="outline"
                          square
                          size="sm"
                          @click="toggleDetails(item, index)"
                        >
                          {{ Boolean(item._toggled) ? 'Hide' : 'Show' }}
                        </CButton>
                      </td>
                    </template>
                    <template #details="{ item }">
                      <CCollapse :visible="Boolean(item._toggled)">
                        <CCardBody>
                          <h4>
                            {{ item.username }}
                          </h4>
                          <p class="text-muted">
                            User since: {{ item.registered }}
                          </p>
                          <CButton size="sm" color="info" class="">
                            User Settings
                          </CButton>
                          <CButton size="sm" color="danger" class="ml-1">
                            Delete
                          </CButton>
                        </CCardBody>
                      </CCollapse>
                    </template>
                  </CSmartTable>
                  <!-- END Smart Table -->
    </div>
  </div>
</template>




<script>
import { CIcon } from '@coreui/icons-vue'
import * as icon from '@coreui/icons'
export default {
  components: {
    CIcon,
  },
  setup() {
    return {
      icon,
    }
  },
}
</script>


<style>
</style>