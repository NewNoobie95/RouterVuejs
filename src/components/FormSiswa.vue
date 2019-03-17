<template>
  <form>
    <div><br>
      <center><table>
        <tr>
          <td><label>NIS</label></td>
          <td><input type="text" name="nis" placeholder="Masukan NIS" /></td>
        </tr>
        <tr>
          <td><label>Nama Lengkap</label></td>
          <td><input type="text" name="nama_lengkap" placeholder="Masukan Nama Lengkap" /></td>
        </tr>
        <tr>
          <td><label>Jenis Kelamin</label></td>
          <td>
            <label><input type="radio" name="jenis_kelamin" value="L"/> L </label>
            <label><input type="radio" name="jenis_kelamin" value="P"/> P </label>
          </td>
        </tr>
        <tr>
          <td><label>Alamat</label></td>
          <td>
            <textarea type="text" name="alamat" placeholder="Masukan Alamat Lengkap">
            </textarea>
          </td>
        </tr>
        <tr>
          <td><label>No Telp</label></td>
          <td><input type="text" name="no_telp" placeholder="Masukan Nomor Telepon" /></td>
        </tr>
        <tr>
          <td><label>Kelas</label></td>
          <td>
            <select>
              <option>
              </option>
            </select>
          </td>
        </tr>
      </table></center>
      <br>
      <button type="submit">Simpan </button>
    </div>
  </form>
</template>

<script>
  export default {

  }
</script>
